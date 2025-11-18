# **CircuitoB. CCTSES ➡️ Empresa**

## **Documentación técnica**

Esta es la documentación técnica de la API del Circuito Integración CCTSES -> Empresa.

---

## **Información general**

- Título: Emmpresa: Circuito integración con CCTESES
- Versión: 1.6
- Base URL: https://{server}:{puerto}/api/integra/cctses/v1

---

??? info "Gráfico de secuencia de operaciones"Operaciones"

    ```mermaid
    sequenceDiagram
        %% Participantes (izquierda a derecha)
        participant CCTSES
        participant Empresa

        %% 1) POST /api/v1/paquetetraslado
        CCTSES->>Empresa: POST /api/v1/paquetetraslado
        Empresa-->>CCTSES: 200 OK Response

        %% 2) PUT /api/v1/paquetetraslado
        CCTSES->>Empresa: PUT /api/v1/paquetetraslado
        Empresa-->>CCTSES: 200 OK Response

        %% 3) POST /api/v1/trasladoasignado
        CCTSES->>Empresa: POST /api/v1/trasladoasignado
        Empresa-->>CCTSES: 200 OK Response

        %% 4) PUT /api/v1/trasladoasignado/{idTrasladoEmpresa}/{idUnidad}
        CCTSES->>Empresa: PUT /api/v1/trasladoasignado/{idTrasladoEmpresa}/{idUnidad}
        Empresa-->>CCTSES: 200 OK Response

        %% 5) DELETE /api/v1/trasladoasignado/{idTrasladoEmpresa}
        CCTSES->>Empresa: DELETE /api/v1/trasladoasignado/{idTrasladoEmpresa}
        Empresa-->>CCTSES: 200 OK Response

        %% 7) POST /api/v1/traslado
        CCTSES->>Empresa: POST /api/v1/traslado
        Empresa-->>CCTSES: 200 OK Response

        %% 9) DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}
        CCTSES->>Empresa: DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}
        Empresa-->>CCTSES: 200 OK Response

        %% 10) PUT /api/v1/traslado/setespera/{trasladoId}
        CCTSES->>Empresa: PUT /api/v1/traslado/setespera/{trasladoId}
        Empresa-->>CCTSES: 200 OK Response

        %% 11) PUT /api/v1/traslado/setnoespera/{trasladoId}
        CCTSES->>Empresa: PUT /api/v1/traslado/setnoespera/{trasladoId}
        Empresa-->>CCTSES: 200 OK Response

        %% 12) GET /api/v1/unidad
        CCTSES->>Empresa: GET /api/v1/unidad
        Empresa-->>CCTSES: 200 OK Response


    ```

## **Operaciones**

1. [POST /api/v1/paquetetraslado](#op-post-api-v1-paquetetraslado)
2. [PUT  /api/v1/paquetetraslado](#op-put-api-v1-paquetetraslado)
3. [POST /api/v1/trasladoasignado](#op-post-api-v1-trasladoasignado)
4. [PUT  /api/v1/trasladoasignado/{idTrasladoCctses}/{idUnidad}](#op-put-api-v1-trasladoasignado-idtrasladocctses-idunidad)
5. [DELETE /api/v1/trasladoasignado/{idTrasladoCctses}](#op-delete-api-v1-trasladoasignado-idtrasladocctses)
6. [POST /api/v1/traslado](#op-post-api-v1-traslado)
7. [DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}](#op-delete-api-v1-traslado-solicitudanula-trasladoids)
8. [PUT  /api/v1/traslado/setespera/{trasladoId}](#op-put-api-v1-traslado-setespera-trasladoid)
9. [PUT  /api/v1/traslado/setnoespera/{trasladoId}](#op-put-api-v1-traslado-setnoespera-trasladoid)
10. [GET  /api/v1/unidad](#op-get-api-v1-unidad)

---

<a id="op-post-api-v1-paquetetraslado"></a>
### **POST /api/v1/paquetetraslado**

Alta de paquete de traslados.

Propiedad | Descripción
:--|:--
Método | POST
Ruta | /api/v1/paquetetraslado
Resumen | Alta de paquete de traslados
Body | application/json: [PaqueteTrasladoAltaCmd_v1](#tipo-paquetetrasladoaltacmd_v1)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path/Query/Header: (ninguno)

#### **Ejemplo de llamada**

```text
POST /api/v1/paquetetraslado
```

#### **Ejemplo de body (request)**

```json
{
  "paquete": {
    "idCCTSES": "PK-2025-0001",
    "codigo": "PK-001",
    "referencia": "REF-ALTA-001",
    "areasTrabajoCd": "AREA1,AREA2",
    "nombre": "Paquete Noviembre",
    "fecha": "2025-11-16T09:00:00Z",
    "traslados": [
      { "idTrasladoCCTSES": "TR-1001" },
      { "idTrasladoCCTSES": "TR-1002" }
    ]
  }
}
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK"
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-put-api-v1-paquetetraslado"></a>
### **PUT /api/v1/paquetetraslado**

Asignar paquete de traslados como enviado correctamete.

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/paquetetraslado
Resumen | Asignar paquete de traslados como enviado correctamete
Body | application/json: [PaqueteTrasladoAltaOkCmd_v1](#tipo-paquetetrasladoaltaokcmd_v1)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path/Query/Header: (ninguno)

#### **Ejemplo de llamada**

```text
PUT /api/v1/paquetetraslado
```

#### **Ejemplo de body (request)**

```json
{
  "idCCTSES": "PK-2025-0001"
}
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK"
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-post-api-v1-trasladoasignado"></a>
### **POST /api/v1/trasladoasignado**

Crea el traslado con información de la unidad que lo debe ejecutar.

Propiedad | Descripción
:--|:--
Método | POST
Ruta | /api/v1/trasladoasignado
Resumen | Crea el traslado con información de la unidad que lo debe ejecutar
Body | application/json: [TrasladoCmd_v1](#tipo-trasladocmd_v1)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path/Query/Header: (ninguno)

#### **Ejemplo de llamada**

```text
POST /api/v1/trasladoasignado
```

#### **Ejemplo de body (request)**

```json
{
  "traslado": {
    "general": {
      "trasladoCctsesId": "389696488962",
      "trasladoExternoId": "",
      "trasladoFecha": "2025-11-15T21:01:00+01:00",
      "trasladoFechaSolicitud": "2025-11-15T21:01:25+01:00",
      "trasladoFechaRecogida": "2025-11-15T21:01:00+01:00",
      "trasladoSentidoCd": "E",
      "TrasladoLinkedId": "",
      "areaServicioCd": "DB",
      "areaServicioTx": "DON BENITO/VILLANUEVA DE LA SERENA",
      "Observaciones": "derivo con oxigeno  a 3 litros por gafas nasales",
      "pacienteIdentificadorURL": null,
      "pacienteInformacionActiva": false,
      "pacienteMovil": "924772550",
      "pacienteMovilSmart": false
    },
    "beneficiario": {
      "nombre": "APELLIDOS, NOMBRE",
      "apellido1": "",
      "apellido2": "",
      "cip": "CIP",
      "nss": "",
      "dni": "",
      "telefono": "999888777",
      "telefonoMovil": "999888777",
      "informacionActiva": false,
      "telefonoMovilSmart": false,
      "generoCd": "1",
      "generoTx": "",
      "fechaNacimiento": "",
      "cap": "",
      "domicilio": {
        "direccion": "CALLE YUSTE 9, RESIDENCIA MAYORES CASTUERA CASTUERA 06420",
        "municipioCd": "0",
        "municipioTx": "",
        "codigoPostal": "06420"
      }
    },
    "transporte": {
      "acompFamiliar": 1,
      "acompMedico": false,
      "acompEnfermero": false,
      "conOxigeno": true,
      "conAyuudante": false,
      "esUvi": false,
      "esAlta": false,
      "esUrgente": true,
      "modalidadCd": "U",
      "modalidadTx": "URGENCIA",
      "modalidadExtraTx": "URGENCIA",
      "tipoAislamientoCd": "",
      "conCovid": false,
      "conVisado": false,
      "prioridadNivel": 8,
      "posicionPacienteCd": "T",
      "posicionPacienteTx": "Camilla",
      "tipo": "C",
      "idUnidad": "Identificador Unidad Asingada"
    },
    "facultativoPrescriptor": {
      "nombre": "NOMBRE",
      "apellido1": "FACULTATIVO PRESCRIPTOR",
      "apellido2": "",
      "nColegiado": "ZZZ858447",
      "areaServicioCd": null
    },
    "origen": {
      "tipoDestinoCd": 1,
      "gpsLocation": {
        "longitud": 0.0,
        "latitud": 0.0
      },
      "domicilio": {
        "direccion": "CALLE YUSTE 9, RESIDENCIA MAYORES CASTUERA CASTUERA 06420",
        "municipioCd": "06036",
        "municipioTx": "CASTUERA",
        "codigoPostal": "06420"
      },
      "centro": null
    },
    "destino": {
      "tipoDestinoCd": 2,
      "gpsLocation": {
        "longitud": 0.0,
        "latitud": 0.0
      },
      "domicilio": null,
      "centro": {
        "centroCCN": "1106000792",
        "centroTx": "HOSPITAL DON BENITO-VILLANUEVA DE LA SERENA",
        "direccion": "HOSPITAL DE DON BENITO-VILLANU (1106000792)"
      }
    }
  }
}
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK",
    "values": [
      {"trasladoEmpresaId": "9885588"}
    ]
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-put-api-v1-trasladoasignado-idtrasladocctses-idunidad"></a>
### **PUT /api/v1/trasladoasignado/{idTrasladoCctses}/{idUnidad}**

Asigna un traslado existente a una unidad específica. idTrasladoCctses e idUnidad en el path.

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/trasladoasignado/{idTrasladoCctses}/{idUnidad}
Resumen | Asigna un traslado existente a una unidad específica. idTrasladoCctses e idUnidad en el path.
Body | (sin cuerpo)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idTrasladoCctses | string | Si | Identificador del traslado en CCTSES
idUnidad | string | Si | Identificador de la unidad a asignar

#### **Ejemplo de llamada**

```text
PUT /api/v1/trasladoasignado/TR-2001/UNI-01
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK"
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-delete-api-v1-trasladoasignado-idtrasladocctses"></a>
### **DELETE /api/v1/trasladoasignado/{idTrasladoCctses}**

Des-asigna la unidad actualmente asociada a un traslado. idTrasladoCctses en el path.

Propiedad | Descripción
:--|:--
Método | DELETE
Ruta | /api/v1/trasladoasignado/{idTrasladoCctses}
Resumen | Des-asigna la unidad actualmente asociada a un traslado
Body | (sin cuerpo)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idTrasladoCctses | string | Si | Identificador del traslado en CCTSES

#### **Ejemplo de llamada**

```text
DELETE /api/v1/trasladoasignado/TR-2001
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK"
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-post-api-v1-traslado"></a>
### **POST /api/v1/traslado**

Crea el traslado desde una orden/comando.

Propiedad | Descripción
:--|:--
Método | POST
Ruta | /api/v1/traslado
Resumen | Crea el traslado desde una orden/comando
Body | application/json: [TrasladoCmd_v1](#tipo-trasladocmd_v1)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path/Query/Header: (ninguno)

#### **Ejemplo de llamada**

```text
POST /api/v1/traslado
```

#### **Ejemplo de body (request)**

```json
{
  "traslado": {
    "general": {
      "trasladoCctsesId": "389696488962",
      "trasladoExternoId": "",
      "trasladoFecha": "2025-11-15T21:01:00+01:00",
      "trasladoFechaSolicitud": "2025-11-15T21:01:25+01:00",
      "trasladoFechaRecogida": "2025-11-15T21:01:00+01:00",
      "trasladoSentidoCd": "E",
      "TrasladoLinkedId": "",
      "areaServicioCd": "DB",
      "areaServicioTx": "DON BENITO/VILLANUEVA DE LA SERENA",
      "Observaciones": "derivo con oxigeno  a 3 litros por gafas nasales",
      "pacienteIdentificadorURL": null,
      "pacienteInformacionActiva": false,
      "pacienteMovil": "924772550",
      "pacienteMovilSmart": false
    },
    "beneficiario": {
      "nombre": "APELLIDOS, NOMBRE",
      "apellido1": "",
      "apellido2": "",
      "cip": "CIP",
      "nss": "",
      "dni": "",
      "telefono": "999888777",
      "telefonoMovil": "999888777",
      "informacionActiva": false,
      "telefonoMovilSmart": false,
      "generoCd": "1",
      "generoTx": "",
      "fechaNacimiento": "",
      "cap": "",
      "domicilio": {
        "direccion": "CALLE YUSTE 9, RESIDENCIA MAYORES CASTUERA CASTUERA 06420",
        "municipioCd": "0",
        "municipioTx": "",
        "codigoPostal": "06420"
      }
    },
    "transporte": {
      "acompFamiliar": 1,
      "acompMedico": false,
      "acompEnfermero": false,
      "conOxigeno": true,
      "conAyuudante": false,
      "esUvi": false,
      "esAlta": false,
      "esUrgente": true,
      "modalidadCd": "U",
      "modalidadTx": "URGENCIA",
      "modalidadExtraTx": "URGENCIA",
      "tipoAislamientoCd": "",
      "conCovid": false,
      "conVisado": false,
      "prioridadNivel": 8,
      "posicionPacienteCd": "T",
      "posicionPacienteTx": "Camilla",
      "tipo": "C"
    },
    "facultativoPrescriptor": {
      "nombre": "NOMBRE",
      "apellido1": "FACULTATIVO PRESCRIPTOR",
      "apellido2": "",
      "nColegiado": "ZZZ858447",
      "areaServicioCd": null
    },
    "origen": {
      "tipoDestinoCd": 1,
      "gpsLocation": {
        "longitud": 0.0,
        "latitud": 0.0
      },
      "domicilio": {
        "direccion": "CALLE YUSTE 9, RESIDENCIA MAYORES CASTUERA CASTUERA 06420",
        "municipioCd": "06036",
        "municipioTx": "CASTUERA",
        "codigoPostal": "06420"
      },
      "centro": null
    },
    "destino": {
      "tipoDestinoCd": 2,
      "gpsLocation": {
        "longitud": 0.0,
        "latitud": 0.0
      },
      "domicilio": null,
      "centro": {
        "centroCCN": "1106000792",
        "centroTx": "HOSPITAL DON BENITO-VILLANUEVA DE LA SERENA",
        "direccion": "HOSPITAL DE DON BENITO-VILLANU (1106000792)"
      }
    }
  }
}
```

#### **Ejemplo de respuesta (200)**

```json
{
  "resultado": {
    "estado": "AA",
    "codigo": "000",
    "descripcion": "OK",
    "values": [
      {"trasladoEmpresaId": "9885588"}
    ]
  }
}
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-delete-api-v1-traslado-solicitudanula-trasladoids"></a>
### **DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}**

Anula uno o varios traslados.

Propiedad | Descripción
:--|:--
Método | DELETE
Ruta | /api/v1/traslado/solicitudanula/{trasladoIDs}
Resumen | Anula uno o varios traslados
Body | (sin cuerpo)
Respuestas | 200: [Response](#tipo-response)

Parámetros

Path y Query

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoIDs (path) | string | Si | Identificador(es) del traslado
trasladoIDs (query) | string |  | ID o IDs de los traslados separados por ,
fechaHora | string(date-time) |  | Fecha de la solicitud de cancelación
idMotivo | string |  | Motivo de anulación (texto libre)
txMotivo | string |  | Texto del motivo de la anulación

#### **Ejemplo de llamada**

```text
DELETE /api/v1/traslado/solicitudanula/TR-1001,TR-1002?fechaHora=2025-11-15T09:00:00Z&idMotivo=SP&txMotivo=Anula%20paciente
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-put-api-v1-traslado-setespera-trasladoid"></a>
### **PUT /api/v1/traslado/setespera/{trasladoId}**

Pone un traslado en estado de espera.

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/traslado/setespera/{trasladoId}
Resumen | Pone un traslado en estado de espera
Body | (sin cuerpo)
Respuestas | 200: [CCTSesResponse](#tipo-cctsesresponse)

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoId | string | Si | Identificador del traslado

#### **Ejemplo de llamada**

```text
PUT /api/v1/traslado/setespera/TR-3001?waitingFrom=2025-11-16T09:00:00Z&enEspera=true
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-put-api-v1-traslado-setnoespera-trasladoid"></a>
### **PUT /api/v1/traslado/setnoespera/{trasladoId}**

Quita el estado de espera a un traslado.

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/traslado/setnoespera/{trasladoId}
Resumen | Quita el estado de espera a un traslado
Body | (sin cuerpo)
Respuestas | 200: [CCTSesResponse](#tipo-cctsesresponse)

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoId | string | Si | Identificador del traslado

#### **Ejemplo de llamada**

```text
PUT /api/v1/traslado/setnoespera/TR-3001
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="op-get-api-v1-unidad"></a>
### **GET /api/v1/unidad**

Devuelve todas las unidades adscritas al servicio de transporte.

Propiedad | Descripción
:--|:--
Método | GET
Ruta | /api/v1/unidad
Resumen | Devuelve todas las unidades adscritas al servicio de transporte
Body | (sin cuerpo)
Respuestas | 200: [UnidadAdscritaDto](#tipo-unidadadscritadto)[]

Parámetros

Path/Query/Header: (ninguno)

#### **Ejemplo de llamada**

```text
GET /api/v1/unidad
```

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---


<a id="tipos-de-datos"></a>
## **Tipos de datos**

<a id="tipo-response"></a>
### **Response**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
resultado | [Result](#tipo-result) |  | Resultado de la operación

<a id="tipo-result"></a>
### **Result**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
estado | string | Si | Resultado de la operación (AA => OK, AE => Error)
codigo | string | Si | Código del resultado
descripcion | string | Si | Descripción del resultado
values | [ResultValues](#tipo-resultvalues) |  | Valores adicionales (clave-valor)

<a id="tipo-resultvalues"></a>
### **ResultValues**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
(adicionales) | string |  | Propiedades adicionales de tipo string

<a id="tipo-paquetetrasladoaltacmd_v1"></a>
### **PaqueteTrasladoAltaCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
paquete | [PaqueteTraslado](#tipo-paquetetraslado) |  | Paquete de traslados

<a id="tipo-paquetetraslado"></a>
### **PaqueteTraslado**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idCCTSES | string | Si | Identificador paquete CCTSES
codigo | string | Si | Código de la planificación
referencia | string | Si | Referencia de la planificación
areasTrabajoCd | string | Si | Lista separada por ',' de las áreas de trabajo
nombre | string | Si | Nombre del paquete
idLote | string |  | Identificador del lote
comentario | string |  | Comentario del paquete
fecha | string(date-time) | Si | Fecha del paquete
traslados | [PaqueteItem](#tipo-paqueteitem)[] | Si | Lista de elementos del paquete

<a id="tipo-paqueteitem"></a>
### **PaqueteItem**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idTrasladoCCTSES | string | Si | Identificador del traslado CCTSES

<a id="tipo-paquetetrasladoaltaokcmd_v1"></a>
### **PaqueteTrasladoAltaOkCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idCCTSES | string | Si | Identificador del paquete confirmado

<a id="tipo-trasladocmd_v1"></a>
### **TrasladoCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
traslado | [Traslado](#tipo-traslado) |  | Datos del traslado

<a id="tipo-traslado"></a>
### **Traslado**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
general | [General](#tipo-general) | Si | Información general del traslado
beneficiario | [Beneficiario](#tipo-beneficiario) |  | Beneficiario
transporte | [Transporte](#tipo-transporte) | Si | Datos del transporte
facultativoPrescriptor | [FactultativoPresciptor](#tipo-factultativopresciptor) |  | Facultativo prescriptor
origen | [Target](#tipo-target) | Si | Origen
destino | [Target](#tipo-target) | Si | Destino

<a id="tipo-general"></a>
### **General**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoCctsesId | string | Si | Id único del traslado en CCTSES
trasladoExternoId | string |  | Id único del traslado en sistema externo
trasladoFecha | string(date-time) |  | Fecha/hora objetivo en destino
trasladoFechaSolicitud | string(date-time) | Si | Fecha de solicitud de la orden
trasladoFechaRecogida | string(date-time) |  | Fecha de recogida en origen
trasladoSentidoCd | string | Si | Sentido: E=Ida, S=Vuelta
trasladoLinkedId | string |  | Id de traslado enlazado (Ida/Vuelta)
areaServicioCd | string | Si | Área sanitaria (código)
areaServicioTx | string | Si | Área sanitaria (texto)
observaciones | string |  | Observaciones

<a id="tipo-beneficiario"></a>
### **Beneficiario**

Propiedad | Tipo | Descripción
:--|:--|:--
nombre | string | Nombre del paciente
nombreCompleto | string | Nombre completo
apellido1 | string | Primer apellido del paciente
apellido2 | string | Segundo apellido del paciente
cip | string | CIP del paciente
nss | string | Nº Seguridad Social del paciente
dni | string | NIF del paciente
telefono | string | Teléfono del paciente
telefonoMovil | string | Teléfono móvil del paciente
generoCd | string | Sexo del paciente: 1-hombre 2-mujer 3-otro
generoTx | string | Sexo del paciente (texto)
fechaNacimiento | string | Fecha de nacimiento del paciente
cap | string | CAP del paciente
domicilio | [Domicilio](#tipo-domicilio) | Domicilio del paciente

<a id="tipo-domicilio"></a>
### **Domicilio**

Propiedad | Tipo | Descripción
:--|:--|:--
direccion | string | Calle/dirección
municipioCd | string | Código CNM del municipio
municipioTx | string | Municipio (texto)
codigoPostal | string | Código postal

<a id="tipo-transporte"></a>
### **Transporte**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
acompFamiliar | integer(int32) | Si | Si lleva acompañante familiar
acompMedico | boolean | Si | Si lleva médico
acompEnfermero | boolean | Si | Si lleva enfermero
conOxigeno | boolean | Si | Si necesita oxígeno
conAyuudante | boolean | Si | Si lleva ayudante
esUvi | boolean | Si | Requiere vehículo tipo UVI
esAlta | boolean | Si | Traslado de alta
esUrgente | boolean | Si | Indica urgencia
modalidadCd | string | Si | Modalidad (código): Consulta, Cura, Diálisis, etc. — Ver tabla: [TB_TRASLADO_MODALIDAD](./CCTSES-doc_funcional.md#tb_traslado_modalidad)
modalidadTx | string |  | Modalidad (texto) — Ver tabla: [TB_TRASLADO_MODALIDAD](./CCTSES-doc_funcional.md#tb_traslado_modalidad)
modalidadExtraTx | string |  | Información adicional de la modalidad (Quimioterapia, Radioterapia...) — Ver tabla: [TB_TRASLADO_TIPO_CONSULTA](./CCTSES-doc_funcional.md#tb_traslado_tipo_consulta)
tipoAislamientoCd | string |  | Tipo de aislamiento: VR (Vía aérea), GT (Gotas), CT (Contacto) — Ver tabla: [TB_TRASLADO_TIPO_AISLAMIENTO](./CCTSES-doc_funcional.md#tb_traslado_tipo_aislamiento)
conCovid | boolean |  | Paciente con Covid
conVisado | boolean | Si | Traslado autorizado (visado)
prioridadNivel | integer(int32) | Si | Prioridad (1=Programado, 5=Medio, 8=Urgente, 10=Emergencia)
posicionPacienteCd | string | Si | Posición: SE (sentado), C (silla ruedas), T (camilla) — Ver tabla: [TB_PACIENTE_POSICION](./CCTSES-doc_funcional.md#tb_paciente_posicion)
posicionPacienteTx | string |  | Posición (texto) — Ver tabla: [TB_PACIENTE_POSICION](./CCTSES-doc_funcional.md#tb_paciente_posicion)
tipo | string | Si | Tipo: I (individual), C (colectivo), M (muestras/órganos) — Ver tabla: [TB_TRASLADO_MODO](./CCTSES-doc_funcional.md#tb_traslado_modo)
idUnidad | string |  | Unidad asignada para la ejecución del traslado (solo si viene pre-asignada por CCTSES)

<a id="tipo-factultativopresciptor"></a>
### **FactultativoPresciptor**

Propiedad | Tipo | Descripción
:--|:--|:--
nombre | string | Nombre del facultativo
apellido1 | string | Primer apellido del facultativo
apellido2 | string | Segundo apellido del facultativo
nColegiado | string | Nº de colegiado

<a id="tipo-target"></a>
### **Target**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
tipoDestinoCd | integer(int32) | Si | Tipo de destino: 1=domicilio, 2=centro sanitario
gpsLocation | [GpsPosition](#tipo-gpsposition) |  | Posición GPS
domicilio | [Domicilio](#tipo-domicilio) |  | Dirección del domicilio
centro | [CentroMedico](#tipo-centromedico) |  | Centro médico

<a id="tipo-gpsposition"></a>
### **GpsPosition**

Propiedad | Tipo | Descripción
:--|:--|:--
longitud | number(double) | Longitud
latitud | number(double) | Latitud

<a id="tipo-centromedico"></a>
### **CentroMedico**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
centroCCN | string | Si | Código Nacional de Centro (10 dígitos)
centroTx | string |  | Nombre/Texto del centro
direccion | string |  | Dirección del centro médico


<a id="tipo-unidadadscritadto"></a>
### **UnidadAdscritaDto**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
(ver esquema) | object |  | Unidad adscrita (vehículo/unidad). — Ver tabla: [TB_SALUD_ZONA](./CCTSES-doc_funcional.md#tb_salud_zona)

---