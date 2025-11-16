# Circuito A: Empresa Concesionaria - CCTSES.

## **Documentación funcional**


## **Tablas de referencia**

### TB_ORDEN_MODALIDAD

Esta tabla recoge la modalidad de un traslado.

| Código | Título                          | Descripción Funcional                                     |
|:-------|:--------------------------------|:----------------------------------------------------------|
| 1      | Consulta                        | Visita programada para evaluación médica o diagnóstico.   |
| 2      | Alta de planta                  | Salida del paciente de una hospitalización en planta.     |
| 3      | Alta de urgencias               | Salida del paciente tras atención en el servicio de urgencias.|
| 4      | Rehabilitación                  | Sesiones o tratamiento para recuperar funciones físicas.|
| 5      | Hemodiálisis                    | Tratamiento de filtración de sangre para pacientes renales.|
| 6      | Traslado Interhospitalario      | Movimiento de un paciente entre diferentes hospitales.    |
| 7      | Quimioterapia HD                | Sesión de quimioterapia en modalidad de hospital de día.  |
| 8      | Radioterapia                    | Tratamiento médico que utiliza radiación para tratar enfermedades.|
| 9      | Traslado fuera comunidad        | Movimiento de un paciente a una ubicación fuera de la comunidad autónoma.|
| 10     | Demencias HD                    | Atenciones específicas para pacientes con demencia en hospital de día.|
| 11     | Diálisis extra                  | Sesión adicional o no programada de diálisis.             |
| 12     | Urgencia                        | Atención médica inmediata por una condición aguda.        |
| 13     | Traslado muestras y órganos     | Transporte especializado de muestras biológicas u órganos para trasplante.|
| 14     | Traslado a domicilio            | Movimiento de un paciente desde el centro médico a su hogar.|
| 15     | Pruebas diagnósticas            | Realización de exámenes o tests para identificar una condición médica.|
| 16     | Ingreso Hospitalario Programado | Admisión planificada de un paciente en un hospital para tratamiento o cirugía.|                                                         |


### TB_GENERO

Esta tabla recoge del los tipos de géneros.

| Código | Título                          | Descripción Funcional                                     |
|:-------|:--------------------------------|:----------------------------------------------------------|
| 1      | Hombre                          | Hombre                                                    |
| 2      | Mujer                          | Mujer                                                    |
| 3      | Otro                            | Otro                                                      |

### TB_SALUD_AREA

Esta tabla recoge las áreas de salud definidas.

| codigo | Descripcion |
| :--- | :--- |
| 0 | OTRAS |
| 1 | CACERES |
| 2 | CORIA |
| 3 | PLASENCIA |
| 4 | NAVALMORAL DE LA MATA |
| 5 | BADAJOZ |
| 6 | DON BENITO/VILLANUEVA DE LA SERENA |
| 7 | LLERENA/ZAFRA |
| 8 | MERIDA |


### TB_PRIORIDAD_TRANSPORTE

Indica la prioridad del transporte.

| codigo | Descripcion |
| :--- | :--- |
| P | Programado |
| U | Urgente |
| S | No Urgente / No Programado |


### TB_PACIENTE_POSICION

Indica la posición del paciente respecto a cómo va ubicado dentro de la ambulancia.

| codigo | Descripcion |
| :--- | :--- |
| SE | Sentado |
| SR | Silla ruedas |
| CA | Camilla |


### TB_TRASLADO_MODO

Indica el tipo de traslado respecto al modo de transporte, indicando qué y cómo se transporta.

| codigo | Descripcion |
| :--- | :--- |
| I | Individual |
| C | Colectivo |
| M | Muestras / órganos |


### TB_TRASLADO_TIPO_VEHICULO

Indica el tipo de vehiculo respecto a la dotación y el uso del mismo.

| codigo | Descripcion |
| :--- | :--- |
| N | No Asistencial |
| B | Bariátrica |
| T | Taxi |
| U | UVI |


### TB_UBICACION_TIPO

Indica el tipo de localización donde hay que recoger o llevar al paciente.

Este tipo de ubicación se utiliza en la información en el apartado `Origen` y `Destino`.

| codigo | Descripcion |
| :--- | :--- |
| 1 | Domicilio |
| 2 | Centro Médico |
| 3 | Otros




