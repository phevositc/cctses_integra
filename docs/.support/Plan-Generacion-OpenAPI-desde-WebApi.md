# Plan detallado para generar un fichero OpenAPI (YAML) desde un proyecto C# WebApi

Fecha: 2025-11-15 21:10

## 1. Propósito y alcance
Este plan explica, paso a paso, cómo generar automáticamente un fichero de especificación OpenAPI (`OpenAPI.yaml`) a partir de un proyecto C# ASP.NET Core WebApi que se escaneará en el momento de la generación. El resultado se utilizará después para:
- 2) Seguir el plan de regeneración de la documentación técnica (`docs/.support/Plan-Regeneracion-CircuitoA.md`).
- 3) Generar el documento funcional (`Circuito-doc_funcional.md`) con las entidades TB_ referenciadas desde el OpenAPI.

Se deben aprovechar las clases existentes de procesado de esquemas:
- `CustomSchemaNameProcessor.cs`: para personalizar el nombre/título de los esquemas.
- `HidePropertySchemaProcessor.cs`: para ocultar propiedades específicas de los modelos.

> Nota: En el repo principal ya constan cambios de `Startup.cs` y existe `HidePropertySchemaProcessor.cs`; asegúrate de usarlos durante la generación.

---

## 2. Requisitos previos
- .NET SDK 6/7/8 instalado (según la versión del proyecto).
- Proyecto WebApi compila correctamente (Release o Debug).
- Comentarios XML habilitados en los proyectos con modelos y controladores.
- Herramientas (al menos una de estas vías):
  - Opción A (recomendada, runtime con Swashbuckle CLI): `dotnet tool install --global Swashbuckle.AspNetCore.Cli`
  - Opción B (runtime por HTTP): capacidad de lanzar la API local y acceder a `/swagger/v1/swagger.json`.
  - Opción C (NSwag CLI por reflexión/auto-host): `dotnet tool install --global NSwag.ConsoleCore` (si la solución usa NSwag).
- Conversor JSON→YAML (elige una):
  - `npx @apidevtools/swagger-cli` (Node/npm)
  - `python -m pip install pyyaml` y script simple

---

## 3. Estructura de salida y nomenclatura
- Salida JSON temporal: `docs/CircuitoA/CircuitoA-openapi.json` (o `docs/ProyectoX/ProyectoX-openapi.json`).
- Salida final YAML: `docs/CircuitoA/CircuitoA-openapi.yaml` (o `docs/ProyectoX/ProyectoX-openapi.yaml`).
- Si el proyecto no es “CircuitoA”, sustituye el prefijo por el nombre del circuito/documento correspondiente.

---

## 4. Preparación del proyecto WebApi
1) Habilitar comentarios XML en los `.csproj` de la API y los modelos compartidos:

```xml
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <NoWarn>$(NoWarn);1591</NoWarn>
  <!-- Opcional: <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\Nombre.Api.xml</DocumentationFile> -->
</PropertyGroup>
```

2) Anotar controladores y acciones:
- Usar `[Produces]`, `[Consumes]`, `[ProducesResponseType]`, `[FromBody]`, `[FromRoute]`, `[FromQuery]`.
- Mantener `summary/remarks` XML en métodos y modelos para que se reflejen en la especificación.

3) Confirmar registro de OpenAPI en `Startup.cs` o `Program.cs` (según estilo del proyecto):
- Si se usa NSwag:

```csharp
// using NSwag;
// using NSwag.Generation.Processors;
// using NJsonSchema.Generation;
services.AddOpenApiDocument(cfg =>
{
    cfg.Title = "API de Integración";
    // Usa los procesadores personalizados presentes en el proyecto
    cfg.SchemaProcessors.Add(new CustomSchemaNameProcessor());
    cfg.SchemaProcessors.Add(new HidePropertySchemaProcessor());
    // Incluir comentarios XML (si el xml está generado)
    var xml = Path.Combine(AppContext.BaseDirectory, "Your.Api.xml");
    if (File.Exists(xml)) cfg.PostProcess = d => d.Info.Description = (d.Info.Description ?? string.Empty);
});
```

- Si se usa Swashbuckle:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new OpenApiInfo { Title = "API de Integración", Version = "v1" });
    var xmlPath = Path.Combine(AppContext.BaseDirectory, "Your.Api.xml");
    if (File.Exists(xmlPath)) c.IncludeXmlComments(xmlPath, includeControllerXmlComments: true);
    // Si existen versiones ISchemaFilter equivalentes a los processors, registrarlas aquí
    // c.SchemaFilter<CustomSchemaNameSchemaFilter>();
    // c.SchemaFilter<HidePropertySchemaFilter>();
});
```

> Importante: Este plan asume que se utilizarán los procesadores existentes `CustomSchemaNameProcessor` y `HidePropertySchemaProcessor`. Mantén su uso alineado con la librería seleccionada (NSwag: `ISchemaProcessor`; Swashbuckle: `ISchemaFilter`).

---

## 5. Generación del OpenAPI (elige 1 vía principal + 1 alternativa)

### Vía A (recomendada) — Swashbuckle CLI “tofile”
1) Compilar la API:

```powershell
# Adaptar ruta del .csproj de la API
 dotnet build .\src\Integra\Empresa\connecta\api\integra.trans.connecta.API.csproj -c Release
```

2) Generar Swagger/OpenAPI JSON desde el ensamblado:

```powershell
# Instalar la CLI si no la tienes
 dotnet tool install --global Swashbuckle.AspNetCore.Cli
# Generar JSON en docs
 dotnet swagger tofile \
   --output .\docs\CircuitoA\CircuitoA-openapi.json \
   .\src\Integra\Empresa\connecta\api\bin\Release\net8.0\integra.trans.connecta.API.dll v1
```

> Esta vía aplica los filtros/configuración registrados en `Startup/Program`, por lo que también se aplicarán `CustomSchemaNameProcessor/HidePropertySchemaProcessor` si están adaptados a Swashbuckle con `SchemaFilter` equivalentes. Si los procesadores son de NSwag, usa la Vía C o ejecuta la API (Vía B).

3) Convertir JSON → YAML:

```powershell
# Con Node
 npm i -g @apidevtools/swagger-cli
 swagger-cli bundle .\docs\CircuitoA\CircuitoA-openapi.json -o .\docs\CircuitoA\CircuitoA-openapi.yaml -t yaml

# Alternativa con Python
 # py -m pip install pyyaml
 py - << 'PY'
import json, yaml, sys
p = r"docs\\CircuitoA\\CircuitoA-openapi.json"
y = r"docs\\CircuitoA\\CircuitoA-openapi.yaml"
with open(p, 'r', encoding='utf-8') as f: data = json.load(f)
with open(y, 'w', encoding='utf-8') as f: yaml.dump(data, f, sort_keys=False, allow_unicode=True)
print('YAML generado en', y)
PY
```

4) Validar:

```powershell
 swagger-cli validate .\docs\CircuitoA\CircuitoA-openapi.yaml
```

---

### Vía B — Runtime por HTTP (API levantada localmente)
1) Levantar la API (perfil Development):

```powershell
 dotnet run --project .\src\Integra\Empresa\connecta\api\integra.trans.connecta.API.csproj
```

2) Descargar el documento JSON:

```powershell
 curl http://localhost:5000/swagger/v1/swagger.json -o .\docs\CircuitoA\CircuitoA-openapi.json
```

3) Convertir a YAML y validar (mismos comandos que en la Vía A).

> Ventaja: Se ejecutan exactamente los procesadores/filters registrados (NSwag o Swashbuckle). Asegura que `CustomSchemaNameProcessor` y `HidePropertySchemaProcessor` están en el pipeline.

---

### Vía C — NSwag CLI (aspnetcore2openapi)
1) Compilar la API:

```powershell
 dotnet build .\src\Integra\Empresa\connecta\api\integra.trans.connecta.API.csproj -c Release
```

2) Generar JSON con NSwag:

```powershell
 dotnet tool install --global NSwag.ConsoleCore
 nswag aspnetcore2openapi \
   /assembly:.\src\Integra\Empresa\connecta\api\bin\Release\net8.0\integra.trans.connecta.API.dll \
   /documentName:v1 \
   /output:.\docs\CircuitoA\CircuitoA-openapi.json
```

3) Convertir a YAML y validar (mismos comandos que en la Vía A).

> Nota: Si los procesadores están implementados como `ISchemaProcessor` y la configuración `AddOpenApiDocument` se registra en `Startup`, NSwag CLI respetará dichos procesadores.

---

## 6. Uso de los procesadores personalizados

### 6.1 CustomSchemaNameProcessor
Objetivo: controlar los nombres finales de los esquemas (por ejemplo, evitar sufijos `Dto` o normalizar mayúsculas/minúsculas).

Pautas de uso:
- Mantener un mapeo consistente `C# → OpenAPI`. Ej.: `StatusInfoCmd` → `StatusInfo`.
- Ajustar `schema.Title` o el nombre en el generador para que coincida con la convención de documentación.
- Evitar colisiones al renombrar (comprobar duplicados).

Buenas prácticas en el código C#:
- Consolidar nombres mediante atributos si el processor los soporta (ej., `[Display(Name="...")]`).
- Añadir pruebas unitarias simples del processor si es posible.

### 6.2 HidePropertySchemaProcessor
Objetivo: excluir del documento OpenAPI propiedades que NO deban publicarse (internas, audit, navegación, etc.).

Pautas de uso:
- Ocultar por atributo (p.ej. `[JsonIgnore]`, o un atributo custom como `[OpenApiHidden]`).
- Opcional: un “allowlist/denylist” por namespace o por patrón de nombre de propiedad.
- Verificar que la ocultación no rompa `required` del modelo.

Checklist mínimo tras aplicar los processors:
- [ ] Los esquemas no contienen nombres internos o temporales.
- [ ] No aparecen propiedades sensibles o internas.
- [ ] Las referencias `$ref` siguen resolviendo correctamente.

---

## 7. Paso 2: Seguir el plan de regeneración de documentación técnica
Una vez generado `OpenAPI.yaml`, continúa con `docs/.support/Plan-Regeneracion-CircuitoA.md` (ya incluido en el repo):
- Actualiza la sección “Información general” con `info.title`, `info.version`, `servers[0].url` del OpenAPI.
- Genera/actualiza por cada operación la tabla principal “Propiedad | Descripción”.
- Extrae “Parámetros” y “Tipos de datos” a bloques `??? info` con tablas de 3 columnas.
- Mantén ejemplos en bloques ```json y llamadas en ```text.
- Revisa y actualiza el diagrama de secuencia Mermaid.
- Añade enlaces a tablas TB_ utilizando las anclas especificadas.

> Para Circuito A, el resultado esperado es un `docs/CircuitoA/circuitoA-doc.md` consistente con la especificación recién generada.

---

## 8. Paso 3: Generar `Circuito-doc_funcional.md` desde `OpenAPI.yaml`
Objetivo: derivar un documento funcional con las entidades TB_ mencionadas en el OpenAPI.

Estrategia de extracción:
1) Escanear `components.schemas` y `paths.*.*.parameters/requestBody` buscando patrones en descripciones que mencionen tablas TB_:
   - Expresión: `TB_[A-Z0-9_]+`
   - Ejemplos: `TB_TRASLADO_ESTADOS`, `TB_VEHICULO_ESTADOS`, `TB_ACTIVIDAD_TIPOS`, `TB_ANULACION_MOTIVOS`, `TB_MOTIVO_ESTADOS`.
2) Construir una lista única ordenada de tablas detectadas y sus “pistas” (campos donde se referencian y breve descripción asociada).
3) Generar `docs/CircuitoA/CircuitoA-doc_funcional.md` (o `docs/<Circuito>/...`) con el formato definido en el plan existente:
   - Encabezado “Entidades funcionales”.
   - Secciones por tabla `### TB_...` con tabla: `Código | Leyenda | Descripción Funcional`.
   - Cuando no se disponga del catálogo completo, incluir placeholders y referencias desde dónde se infirió (campo y esquema del OpenAPI).
   - Incluir, si aplica, bloques “Tipo: …” con “Titulo de Recurso: …” para agrupar (VEHICULO, TRASLADO, JORNADA, GENÉRICO).

Plantilla mínima (ejemplo):

```
### TB_TRASLADO_ESTADOS

Descripción breve: Estados del ciclo de vida del traslado (inferidos desde `Status.idEstadoTraslado`).

| Código | Leyenda | Descripción Funcional |
|:--|:--|:--|
| P | PENDIENTE | … |
| A | ASIGNADO | … |
| … | … | … |
```

> Si el OpenAPI NO aporta los catálogos TB_ explícitos, documenta la referencia, deja la tabla con placeholders y enlaza a la fuente funcional oficial (cuando exista) para su completado manual.

---

## 9. Automatización (script PowerShell sugerido)
Ejemplo de script unificado (`scripts/generar-openapi.ps1`) para Vía A + YAML + validación:

```powershell
param(
  [string]$Csproj = "src/Integra/Empresa/connecta/api/integra.trans.connecta.API.csproj",
  [string]$OutJson = "docs/CircuitoA/CircuitoA-openapi.json",
  [string]$OutYaml = "docs/CircuitoA/CircuitoA-openapi.yaml",
  [string]$DllRel = "src/Integra/Empresa/connecta/api/bin/Release/net8.0/integra.trans.connecta.API.dll",
  [string]$DocName = "v1"
)

# 1) Build
Write-Host "[1/4] Compilando API..."
dotnet build $Csproj -c Release | Out-Host

# 2) Generar JSON (Swashbuckle CLI)
Write-Host "[2/4] Generando OpenAPI JSON..."
dotnet swagger tofile --output $OutJson $DllRel $DocName | Out-Host

# 3) Convertir a YAML
Write-Host "[3/4] Convirtiendo a YAML..."
if (-not (Get-Command swagger-cli -ErrorAction SilentlyContinue)) {
  npm i -g @apidevtools/swagger-cli | Out-Host
}
swagger-cli bundle $OutJson -o $OutYaml -t yaml | Out-Host

# 4) Validar
Write-Host "[4/4] Validando YAML..."
swagger-cli validate $OutYaml | Out-Host

Write-Host "Listo: $OutYaml"
```

---

## 10. Calidad y validaciones
- [ ] `openapi` = 3.0.x y `info` completo (title, version, description opcional).
- [ ] `servers[0].url` correcto (prod/pre/dev).
- [ ] Esquemas con nombres finales acordados (processor aplicado).
- [ ] Propiedades ocultas no aparecen en los modelos públicos (processor aplicado).
- [ ] Todas las acciones REST expuestas por la API aparecen en `paths` con sus respuestas 2xx/4xx/5xx.
- [ ] JSON→YAML correcto y validado por `swagger-cli`.

---

## 11. Problemas frecuentes y soluciones
- No aparecen los comentarios XML en OpenAPI → comprobar `<GenerateDocumentationFile>true</...>` y que `IncludeXmlComments`/`AddOpenApiDocument` los esté leyendo.
- Los procesadores no se aplican → verifica que estás usando la vía que carga el pipeline de OpenAPI registrado (Vía B o Vía C con NSwag). Swashbuckle CLI no ejecutará processors de NSwag; necesitarías SchemaFilters equivalentes o usar runtime/NSwag.
- El CLI no encuentra el `dll` → confirma `-c Release`, `TargetFramework` (net6.0/net7.0/net8.0) y rutas.
- YAML con `null` o `oneOf` extraño → suele ocurrir al ocultar propiedades requeridas; revisa `required` del esquema tras `HidePropertySchemaProcessor`.

---

## 12. Entregables esperados
1) `docs/CircuitoA/CircuitoA-openapi.yaml` generado desde el código.
2) Documentación técnica actualizada siguiendo `docs/.support/Plan-Regeneracion-CircuitoA.md`.
3) `docs/CircuitoA/CircuitoA-doc_funcional.md` generado/actualizado con las entidades TB_ detectadas en el OpenAPI.

---

## 13. Plantillas rápidas

### 13.1 Encabezado de operación en doc técnica
```
N) METHOD /ruta/

| Propiedad | Descripción |
|:--|:--|
| Método | METHOD |
| Ruta | /ruta/ |
| operationId | opId |
| Resumen | … |
| Descripción | … |
| Body | application/json: Modelo |
| Respuestas | 201: Response<br>400: Response<br>500: Response |

??? info "Parámetros"

    Path

    | Propiedad | Tipo | Descripción |
    |:--|:--|:--|
    | id | string | Requerido. |

??? info "Tipos de datos"

    Modelo

    | Propiedad | Tipo | Descripción |
    |:--|:--|:--|
    | campo | tipo | … |
```

### 13.2 Sección TB_ en doc funcional
```
### TB_XYZ

| Código | Leyenda | Descripción Funcional |
|:--|:--|:--|
| ... | ... | ... |
```

---

## 14. Cronograma sugerido (por ejecución)
- T0: Preparación del entorno y build (10 min)
- T0+10: Generación JSON (2–5 min)
- T0+15: Conversión a YAML + validación (5 min)
- T0+25: Actualización docs técnica (30–60 min, según cambios)
- T0+90: Generación/ajuste doc funcional (30–60 min)

---

## 15. Control final
- [ ] `CircuitoA-openapi.yaml` actualizado hoy
- [ ] Doc técnica sincronizada
- [ ] Doc funcional sincronizada y con enlaces TB_ válidos
- [ ] Navegación de mkdocs.yml permite acceder a ambos documentos

---

Autoría: Equipo de Documentación Técnica
Ubicación del presente plan: `docs/.support/Plan-Generacion-OpenAPI-desde-WebApi.md`