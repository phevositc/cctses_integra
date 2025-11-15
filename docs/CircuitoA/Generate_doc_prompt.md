### Estrategia de Fusión de Contexto

Para que esto funcione, debes proporcionar a la IA dos "inputs" claros.
1.  **Input A (Técnico):** El contenido del `openapi.yaml`.
2.  **Input B (Negocio):** El contenido de tu archivo `entidades.md`.

### El Prompt "Maestro"

Copia y pega el siguiente prompt. He incluido marcadores `[PASTA AQUÍ...]` para que sepas dónde poner tu información.

***

**Rol:** Actúa como un Technical Writer Senior especializado en integración de sistemas y APIs REST. Tu objetivo es generar una "Guía de Integración" cohesiva y profesional dirigida a un desarrollador externo.

**Entradas:**
Vas a recibir dos fuentes de información que debes combinar:
1.  **ESPECIFICACIÓN TÉCNICA (YAML):** Contiene la estructura exacta de la API, tipos de datos, endpoints y ejemplos técnicos.
2.  **DICCIONARIO FUNCIONAL (MARKDOWN):** Contiene descripciones detalladas del negocio, tablas de códigos, explicaciones de las entidades y reglas funcionales que no caben en el YAML.

**Instrucciones de Fusión (Crucial):**
*   **Prioridad:** Para nombres de campos, rutas y tipos de datos, el YAML es la verdad absoluta. Para descripciones, contexto de negocio y tablas de valores (leyendas), el MARKDOWN tiene prioridad y debe enriquecer al YAML.
*   **Mapeo:** Cuando encuentres una entidad en el YAML (ej: `EstadoPedido`), busca su correspondiente en el MARKDOWN. Si en el Markdown hay una tabla de códigos (ej: 1=Recibido, 2=En preparación), debes incluir esa tabla explícitamente en la documentación final.
*   **Información Funcional:** Extrae los datos de SLA (tiempos de respuesta) y frecuencia de los campos `x-response-time-sla` y `x-data-frequency` del YAML y redáctalos en un lenguaje natural y claro en una sección dedicada.

**Estructura del Documento a Generar:**
Genera la salida en formato Markdown limpio, siguiendo estrictamente esta estructura:

1.  **Introducción y Circuito:**
    *   Título y Versión (del YAML).
    *   Descripción de la operativa (del campo `description` del YAML y contexto del Markdown). Explicar el flujo paso a paso.
2.  **Información Funcional y SLAs:**
    *   Detalla los tiempos de respuesta esperados, frecuencias de actualización y cualquier restricción operativa (extraído de los campos `x-` del YAML y notas del Markdown).
4.  **Diccionario de Entidades (El punto fuerte):**
    *   Para cada entidad principal, crea una sección.
    *   Muestra la estructura JSON (del YAML).
    *   Añade la tabla descriptiva o leyenda de valores (del MARKDOWN). *Esto es fundamental: quiero ver qué significa cada código.*
5.  **Referencia de Operaciones (Endpoints):**
    *   Agrupa por Tags.
    *   Para cada endpoint: Método, URL, Descripción corta.
    *   Parámetros requeridos.
    *   **Importante:** No pongas JSONs gigantes aquí, referencia las entidades definidas en el punto 4. 
7.  **Ejemplos de Uso:**
    *   Muestra ejemplos de uso de cada endpoint.

**Puntos importantes:**

- La documentación tiene que ser en formato Markdown, profesional, indicando cada operación en detalle.
- La documentación debe extensa, con ejemplos de uso y referencias a las entidades definidas.

dar

---