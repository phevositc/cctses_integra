## **CCTSES — Documentación técnica (a partir de OpenAPI)**

Fecha de generación: 2025-11-15 21:46

## **Información general**

- Título: Emmpresa: Circuito integración con CCTESES
- Versión: 1.6
- Base URL: https://{server}:{puerto}/api/integra/cctses/v1.

---

## **Operaciones**

1. POST /api/v1/planificacion
2. PUT  /api/v1/planificacion
3. PUT  /api/v1/propuesta
4. GET  /api/v1/traslado/cs
5. POST /api/v1/traslado
6. DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}
7. PUT /api/v1/traslado/setespera/{trasladoId}
8. PUT /api/v1/traslado/setnoespera/{trasladoId}

---

### **POST /api/v1/planificacion**

Propiedad | Descripción
:--|:--
Método | POST
Ruta | /api/v1/planificacion
operationId | Planificacion_post
Resumen | Alta-planificacion
Body | application/json: PlanificacionAltaCmd_v1
Respuestas | 200: CCTSesResponse

Parámetros

- Path: (ninguno)
- Query: (ninguno)
- Header: (ninguno)

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **PUT /api/v1/planificacion**

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/planificacion
operationId | Planificacion_put
Resumen | Alta-planificacion
Body | application/json: PlanificacionAltaOkCmd_v1
Respuestas | 200: CCTSesResponse

Parámetros

Path/Query/Header: (ninguno)

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **PUT /api/v1/propuesta**

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/propuesta
operationId | Propuesta_put
Resumen | Alta-planificacion
Body | application/json: PropuestaStatusCmd_v1
Respuestas | 200: CCTSesResponse

Parámetros

Path/Query/Header: (ninguno)

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **GET /api/v1/traslado/cs**

Propiedad | Descripción
:--|:--
Método | GET
Ruta | /api/v1/traslado/cs
operationId | Traslado_getCurrentState
Resumen | Devuelve el estado de todos los traslados indicados en el filtro
Respuestas | 200: TrasladoStateDto[]

Parámetros

Query

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
day | string(date-time) |  | Día a consultar

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **POST /api/v1/traslado**

Propiedad | Descripción
:--|:--
Método | POST
Ruta | /api/v1/traslado
operationId | Traslado_post
Resumen | Crea el traslado desde una orden/comando
Body | application/json: TrasladoCmd_v1
Respuestas | 200: CCTSesResponse

Parámetros

Path/Query/Header: (ninguno)

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **DELETE /api/v1/traslado/solicitudanula/{trasladoIDs}**

Propiedad | Descripción
:--|:--
Método | DELETE
Ruta | /api/v1/traslado/solicitudanula/{trasladoIDs}
operationId | Traslado_trasladoSolicitudAnula
Resumen | Anula uno o varios traslados
Respuestas | 200: CCTSesResponse

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoIDs | string | ? | Identificadores de traslado en la ruta

Query

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
requestId | string |  | Identificador de la solicitud específica
requestSource | string |  | Origen de la solicitud
trasladoIDs | string |  | ID o IDs de los traslados separados por ,
fechaHora | string(date-time) |  | Fecha de la solicitud de cancelación
idMotivo | string |  | Motivo de anulación (texto libre)
txMotivo | string |  | Texto del motivo de la anulación

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **PUT /api/v1/traslado/setespera/{trasladoId}**

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/traslado/setespera/{trasladoId}
operationId | Traslado_putPacienteEnEspera
Resumen | Establece el estado paciente-en-espera sobre un traslado
Respuestas | 200: CCTSesResponse

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoId | string | ? | Traslado identificador

Query

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
waitingFrom | string(date-time) |  | Fecha y hora (UTC) del momento en que se pone en espera
enEspera | boolean |  | Indica si el traslado está en espera (por defecto, false)

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

### **PUT /api/v1/traslado/setnoespera/{trasladoId}**

Propiedad | Descripción
:--|:--
Método | PUT
Ruta | /api/v1/traslado/setnoespera/{trasladoId}
operationId | Traslado_putPacunsetenesperaienteNoEnEspera
Resumen | Desmarca el estado paciente-en-espera sobre un traslado
Respuestas | 200: CCTSesResponse

Parámetros

Path

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoId | string | ? | Traslado identificador

Tipos de datos: ver sección [Tipo de datos](#tipos-de-datos).

---

<a id="tipos-de-datos"></a>
## **Tipos de datos**

### **PlanificacionAltaCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
planificacion | Planificacion |  | Comando para enviar planificación a la empresa

### **Planificacion**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idCCTSES | string | Si | Identificador planifición CCTSES
codigo | string | Si | Código de la planificación
referencia | string | Si | Referencia de la planificación
areasTrabajoCd | string | Si | Lista separada por ',' de las áreas de trabajo
nombre | string | Si | Nombre de la planificación
idLote | string | Si | Identificador del lote
comentario | string |  | Comentario de la planificación
fecha | string(date-time) | Si | Fecha de la planificación
rutas | Ruta[] | Si | Rutas de la planificación

### **Ruta**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idRutaCCTSES | string | Si | Identificador ruta CCTSES
idCodigoCCTSES | string | Si | Código ruta CCTSES
referencia | string |  | Referencia de la ruta
horaLlegada | string | Si | Hora llegada a destino
unidadCodigo | string |  | Código de la unidad (recurso) que ejecutará la ruta
sentido | string | Si | Sentido: E=Entrada(Ida), S=Salida(Retorno)
esLocalizado | integer(int32) | Si | 1 si la unidad-vehículo está geolocalizada; 0 si no
municipioCd | string |  | Código CNM del municipio
unidadBaseLatitud | string |  | Latitud de la base de la unidad
unidadBaseLongitud | string |  | Longitud de la base de la unidad
unidadLocalidadCd | string |  | Localidad (código) de la base de la unidad
idRutaVinculadaCCTSES | string |  | Id de la ruta vinculada (IDA/VUELTA)
traslados | RutaTraslado[] |  | Traslados incluidos
tramos | RutaTramo[] |  | Tramos de la ruta
incidencias | RutaIncidencia[] |  | Incidencias de la ruta

### **RutaTraslado**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idTrasladoCCTSES | string | Si | Identificador traslado CCTSES

### **RutaTramo**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idTramoCCTSES | string | Si | Identificador tramo CCTSES
orden | integer(int32) | Si | Nº de orden del tramo
origenLongitud | string |  | Origen longitud
origenLatitud | string |  | Origen latitud
origenMunicipioCd | string | Si | Código CNM municipio de origen
destinoLongitud | string |  | Destino longitud
destinoLatitud | string |  | Destino latitud
destinoMunicipioCd | string | Si | Código CNM municipio de destino
duration | integer(int32) |  | Duración estimada tramo (segundos)
recepcionTrayecto | integer(int32) |  | Recepción trayecto (segundos)

### **RutaIncidencia**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
id | string | Si | Incidencia identificador
code | string | Si | Incidencia código
description | string |  | Descripción de la incidencia

### **PlanificacionAltaOkCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
idCCTSES | string | Si | Identificador planifición CCTSES

### **PropuestaStatusCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
requestId | string |  | 
requestSource | string |  | 
idIntegracion | string | Si | Identificador planifición CCTSES
estado | string | Si | Estado de la propuesta

### **TrasladoStateDto**

Propiedad | Tipo | Descripción
:--|:--|:--
td | string | Traslado Identificador
tm | string | Traslado conductor nombre (date-time? nullable)
tt | string(date-time) | Fecha del traslado
ts | string | Código de estado del traslado
u | string | Traslado unidad
ua | string | Código Administrativo de unidad
m | string | Matrícula
codgrt | string | Código agrupación por recorrido/día
d | string | Traslado conductor nombre
ssinfo | StateInfo[] | Información de estados
tms | TerminalStateInfo | Estado terminal

### **StateInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
timestamp | string(date-time) | Fecha-hora del estado
stateCode | string | Código del estado

### **TerminalStateInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
j | JournalInfo | Información de journal
g | GpsInfo | Información GPS

### **JournalInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
id | string | Identificador del journal
source | string | Origen
created | string(date-time) | Fecha creación
usuario | string | Usuario
deviceId | string | Dispositivo

### **GpsInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
lat | number(double) | Latitud
lon | number(double) | Longitud
r | integer(int32) | —
spd | integer(int32) | Velocidad
tst | integer(int32) | Timestamp

### **TrasladoCmd_v1**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
traslado | Traslado |  | Datos del traslado

### **Traslado**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
general | General | Si | Información general del traslado
beneficiario | Beneficiario |  | Beneficiario
transporte | Transporte | Si | Datos del transporte
facultativoPrescriptor | FactultativoPresciptor |  | Facultativo prescriptor
origen | Target | Si | Origen
destino | Target | Si | Destino

### **General**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
trasladoCctsesId | string | Si | Id único del traslado en CCTSES
trasladoExternoId | string |  | Id único del traslado en sistema externo
trasladoPlanificacionIdCCTSES | string |  | Id planificación en CCTSES
trasladoPlanificacionRutaIdCCTSES | string |  | Id planificación-ruta en CCTSES
trasladoPlanificacionRutaCdCCTSES | string |  | Código planificación-ruta en CCTSES
trasladoPlanficacionUnidadTransporte | string |  | Unidad transporte planificada
trasladoRutaId | string |  | Id ruta (si no está planificado)
trasladoFecha | string(date-time) |  | Fecha/hora objetivo en destino
trasladoFechaSolicitud | string(date-time) | Si | Fecha de solicitud de la orden
trasladoFechaRecogida | string(date-time) |  | Fecha de recogida en origen
trasladoSentidoCd | string | Si | Sentido: E=Ida, S=Vuelta
trasladoLinkedId | string |  | Id de traslado enlazado (Ida/Vuelta)
areaServicioCd | string | Si | Área sanitaria (código)
areaServicioTx | string | Si | Área sanitaria (texto)
observaciones | string |  | Observaciones

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
domicilio | Domicilio | Domicilio del paciente

### **Domicilio**

Propiedad | Tipo | Descripción
:--|:--|:--
direccion | string | Calle/dirección
municipioCd | string | Código CNM del municipio
municipioTx | string | Municipio (texto)
codigoPostal | string | Código postal

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
modalidadCd | string | Si | Modalidad (código): Consulta, Cura, Diálisis, etc.
modalidadTx | string |  | Modalidad (texto)
modalidadExtraTx | string |  | Información adicional de la modalidad (Quimioterapia, Radioterapia...)
tipoAislamientoCd | string |  | Tipo de aislamiento: VR (Vía aérea), GT (Gotas), CT (Contacto)
conCovid | boolean |  | Paciente con Covid
conVisado | boolean | Si | Traslado autorizado (visado)
prioridadNivel | integer(int32) | Si | Prioridad (1=Programado, 5=Medio, 8=Urgente, 10=Emergencia)
posicionPacienteCd | string | Si | Posición: SE (sentado), C (silla ruedas), T (camilla)
posicionPacienteTx | string |  | Posición (texto)
tipo | string | Si | Tipo: I (individual), C (colectivo), M (muestras/órganos)

### **FactultativoPresciptor**

Propiedad | Tipo | Descripción
:--|:--|:--
nombre | string | Nombre del facultativo
apellido1 | string | Primer apellido del facultativo
apellido2 | string | Segundo apellido del facultativo
nColegiado | string | Nº de colegiado

### **Target**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
tipoDestinoCd | integer(int32) | Si | Tipo de destino: 1=domicilio, 2=centro sanitario
gpsLocation | GpsPosition |  | Posición GPS
domicilio | Domicilio |  | Dirección del domicilio
centro | CentroMedico |  | Centro médico

### **GpsPosition**

Propiedad | Tipo | Descripción
:--|:--|:--
longitud | number(double) | Longitud
latitud | number(double) | Latitud

### **CentroMedico**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
centroCCN | string | Si | Código Nacional de Centro (10 dígitos)
centroTx | string |  | Nombre/Texto del centro
direccion | string |  | Dirección del centro médico

### **UnidadStateDto**

Propiedad | Tipo | Descripción
:--|:--|:--
unidad | string | 
unidadAdmCode | string | 
unidadActividadCode | string | 
unidadActividadName | string | 
unidadCentroCode | string | Codigo del centro al que pertenece la Unidad
unidadCentroName | string | Nombre del centro al que pertenece la Unidad
unidadAreaCode | string | Codigo del area al que pertenece la Unidad
unidadAreaName | string | Nombre del área al que pertenece la Unidad
matricula | string | 
journal | JournalStateDto | 
gps | GpsInfo2 | 
moveState | MovementStateInfo | 
specialState | SpecialStateInfo | 
connection | ConnectionInfo | 
state | integer(int32) | Estado del terminal
lastTimestamp | string(date-time) | Fecha del ultimo estado
lastReception | string(date-time) | Fecha de la ultima recepción de información
nextTrasladoTimeLeft | integer(int32) | Minutos resta para ejecutar el siguiente traslado

### **JournalStateDto**

Propiedad | Tipo | Descripción
:--|:--|:--
personalId | number(decimal) | 
personalNombre | string | 
personalTelefono | string | 
state | integer(int32) | 1: abierto, 0:cerrado
timestamp | string(date-time) | Fecha produjoj el estado
journalId | string | 

### **GpsInfo2**

Propiedad | Tipo | Descripción
:--|:--|:--
latitud | number(double) | 
longitud | number(double) | 
altitud | integer(int32) | 
rumbo | integer(int32) | 
velocidad | integer(int32) | 
geoaddress | string | 
geociudad | string | 

### **MovementStateInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
state | integer(int32) | 0: parado 1:marcha
timestampStopped | string(date-time) | Indica fecha produjo el estado
timestamp | string(date-time) | Fecha desde estado está activo

### **SpecialStateInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
state | integer(int32) | 0: ninguno 1:mod-comida 2:modo-mnto
timestamp | string(date-time) | Indica fecha produjo el estado

### **ConnectionInfo**

Propiedad | Tipo | Descripción
:--|:--|:--
state | integer(int32) | 0: no-conectado 1:conectado
timestamp | string(date-time) | Indica fecha produjo el estado

### **CCTSesResponse**

Propiedad | Tipo | Descripción
:--|:--|:--
resultado | Result | Resultado de la operación

### **Result**

Propiedad | Tipo | Requerido | Descripción
:--|:--|:--:|:--
estado | string | Si | Resultado de la operación (p. ej., AA=ok, AE=Error)
codigo | string | Si | Código del resultado
descripcion | string | Si | Descripción del resultado
values | ResultValues |  | Mapa de valores adicionales

### **ResultValues**

Propiedad | Tipo | Descripción
:--|:--|:--
[clave] | string | Valor asociado