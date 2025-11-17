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
| CA | CACERES |
| CO | CORIA |
| PL | PLASENCIA |
| NA | NAVALMORAL DE LA MATA |
| BA | BADAJOZ |
| DB | DON BENITO/VILLANUEVA DE LA SERENA |
| LL | LLERENA/ZAFRA |
| ME | MERIDA |


### TB_SALUD_ZONA

Esta tabla recoge las zonas de salud definidas. Estas zonas corresponde con los centros de salud.

??? info "Tabla Zonas de Salud"

    | Código | Descripción                                 |
    |:-------|:--------------------------------------------|
    | AA     | ACEUCHAL                                    |
    | AB     | AHIGAL                                      |
    | AC     | ALBURQUERQUE                                |
    | AD     | ALCANTARA                                   |
    | AE     | ALCONCHEL                                   |
    | AF     | ALCUESCAR                                   |
    | AG     | ALDEACENTENERA                              |
    | AH     | ALDEANUEVA DE LA VERA                       |
    | AI     | ALDEANUEVA DEL CAMINO                       |
    | AJ     | ALMARAZ                                     |
    | AK     | ALMENDRALEJO                                |
    | AL     | ARROYO DE LA LUZ                            |
    | AM     | ARROYO DE SAN SERVAN                        |
    | AN     | AZUAGA                                      |
    | AO     | BADAJOZ                                     |
    | AP     | BARCARROTA                                  |
    | AQ     | BERLANGA                                    |
    | AR     | BERZOCANA                                   |
    | AS     | BOHONAL DE IBOR                             |
    | AT     | CABEZA DEL BUEY                             |
    | AU     | CABEZUELA DEL VALLE                         |
    | AV     | CACERES                                     |
    | AW     | CALAMONTE                                   |
    | AX     | CAMINOMORISCO                               |
    | AY     | CAMPANARIO                                  |
    | AZ     | CAMPILLO DE LLERENA                         |
    | BA     | CAÑAMERO                                    |
    | BB     | CAÑAVERAL                                   |
    | BC     | CASAR DE CACERES                            |
    | BD     | CASAS DEL CASTAÑAR                          |
    | BE     | CASTAÑAR DE IBOR                            |
    | BF     | CASTUERA                                    |
    | BG     | CECLAVIN                                    |
    | BH     | CEDILLO                                     |
    | BI     | CILLEROS                                    |
    | BJ     | CORDOBILLA DE LACARA                        |
    | BK     | CORIA                                       |
    | BL     | DELEITOSA                                   |
    | BM     | DON BENITO                                  |
    | BN     | DON BENITO - VILLANUEVA DE LA SERENA        |
    | BO     | ELJAS                                       |
    | BP     | FREGENAL DE LA SIERRA                       |
    | BQ     | FUENTE DE CANTOS                            |
    | BR     | FUENTE DEL MAESTRE                          |
    | BS     | GEVORA                                      |
    | BT     | GUADALUPE                                   |
    | BU     | GUAREÑA                                     |
    | BV     | HELECHOSA DE LOS MONTES                     |
    | BW     | HERRERA DEL DUQUE                           |
    | BX     | HERVAS                                      |
    | BY     | HORNACHOS                                   |
    | BZ     | HOYOS                                       |
    | CA     | JARAIZ DE LA VERA                           |
    | CB     | JARANDILLA DE LA VERA                       |
    | CC     | JEREZ DE LOS CABALLEROS                     |
    | CD     | LA ROCA DE LA SIERRA                        |
    | CE     | LA ZARZA                                    |
    | CF     | LLERENA                                     |
    | CG     | LOGROSAN                                    |
    | CH     | LOS SANTOS DE MAIMONA                       |
    | CI     | LOSAR DE LA VERA                            |
    | CJ     | MADROÑERA                                   |
    | CK     | MALPARTIDA DE CACERES                       |
    | CL     | MEMBRIO                                     |
    | CM     | MERIDA                                      |
    | CN     | MIAJADAS                                    |
    | CO     | MOHEDAS DE GRANADILLA                       |
    | CP     | MONESTERIO                                  |
    | CQ     | MONTEHERMOSO                                |
    | CR     | MONTERRUBIO DE LA SERENA                    |
    | CS     | MONTIJO                                     |
    | CT     | MORALEJA                                    |
    | CU     | NAVALMORAL DE LA MATA                       |
    | CV     | NAVALVILLAR DE PELA                         |
    | CW     | NAVAS DEL MADROÑO                           |
    | CX     | NAVE CACERES                                |
    | CY     | NAVEZUELAS                                  |
    | CZ     | NUÑOMORAL                                   |
    | DA     | OLIVA DE LA FRONTERA                        |
    | DB     | OLIVENZA                                    |
    | DC     | ORELLANA LA VIEJA                           |
    | DD     | PINOFRANQUEADO                              |
    | DE     | PLASENCIA                                   |
    | DF     | PUEBLA DEL MAESTRE                          |
    | DG     | PUEBLONUEVO DEL GUADIANA                    |
    | DH     | QUINTANA DE LA SERENA                       |
    | DI     | RIBERA DEL FRESNO                           |
    | DJ     | SALORINO                                    |
    | DK     | SAN VICENTE DE ALCANTARA                    |
    | DL     | SANTA AMALIA                                |
    | DM     | SANTA MARTA DE LOS BARROS                   |
    | DN     | SANTIAGO DE ALCÁNTARA                       |
    | DO     | SEGURA DE LEON                              |
    | DP     | SERRADILLA                                  |
    | DQ     | SIRUELA                                     |
    | DR     | SOLANA DE LOS BARROS                        |
    | DS     | TALARRUBIAS                                 |
    | DT     | TALAVAN                                     |
    | DU     | TALAVERA LA REAL                            |
    | DV     | TALAYUELA                                   |
    | ED     | TORRE DE DON MIGUEL                         |
    | EE     | TORRECILLAS DE LA TIESA                     |
    | EF     | TORREJONCILLO                               |
    | EG     | TRUJILLO                                    |
    | EH     | VALDEFUENTES                                |
    | EI     | VALENCIA DE ALCANTARA                       |
    | EJ     | VALENCIA DEL MOMBUEY                        |
    | EK     | VALENCIA DEL VENTOSO                        |
    | EL     | VALVERDE DE LEGANES                         |
    | EM     | VALVERDE DEL FRESNO                         |
    | EN     | VILLAFRANCA DE LOS BARROS                   |
    | EO     | VILLANUEVA DE LA SERENA                     |
    | EP     | VILLANUEVA DE LA SIERRA                     |
    | EQ     | VILLANUEVA DE LA VERA                       |
    | ER     | VILLANUEVA DEL FRESNO                       |
    | ES     | VILLAR DEL PEDROSO                          |
    | ET     | VILLARTA DE LOS MONTES                      |
    | EU     | ZAFRA                                       |
    | EV     | ZAHINOS                                     |
    | EW     | ZALAMEA DE LA SERENA                        |
    | EX     | ZARZA DE GRANADILLA                         |
    | EY     | ZORITA                                      |

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
| S | Sentado |
| C | Silla ruedas |
| T | Camilla |


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

### TB_TRASLADO_MODALIDAD

Indica la modalidad del traslado.

| codigo | descripción |
| :--- | :--- |
| U | URGENCIA |
| O | CONSULTA |
| C | CURA |
| D | DIALISIS |
| RH | REHABILITACION |
| T | TERAPIA |
| A | ALTA |

### TB_TRASLADO_TIPO_CONSULTA

Indica el tipo de consulta del traslado.

| Código | Descripción                       |
|:-------|:----------------------------------|
| AP     | ALTA PLANTA                       |
| AU     | ALTA URGENCIAS                    |
| CO     | CONSULTA                          |
| DH     | DEMENCIAS HD                      |
| DE     | DIALISIS EXTRA                    |
| HE     | HEMODIALISIS                      |
| IN     | INGRESO HOSP.NO-PROGRAMADO        |
| PD     | PRUEBAS DIAGNOSTICAS              |
| QH     | QUIMIOTERAPIA HD                  |
| RT     | RADIOTERAPIA                      |
| RE     | REHABILITACION                    |
| TD     | TRASLADO A DOMICILIO              |
| TC     | TRASLADO FUERA COMUNIDAD          |
| TI     | TRASLADO INTERHOSPITALARIO        |
| TM     | TRASLADO MUESTRAS Y ÓRGANOS       |
| UR     | URGENCIA                          |


### TB_UBICACION_TIPO

Indica el tipo de localización donde hay que recoger o llevar al paciente.

Este tipo de ubicación se utiliza en la información en el apartado `Origen` y `Destino`.

| codigo | Descripcion |
| :--- | :--- |
| 1 | Domicilio |
| 2 | Centro Médico |
| 3 | Otros


### TB_AISLAMIENTO_TIPO

Indica el tipo de aislamiento que requiere el paciente.

| Código | Descripción                       |
|:-------|:----------------------------------|
| VR | Vía Aérea                               |
| GT | Gotas                                     |
| CT | Contacto                                  |


### TB_TRASLADO_NIVEL_PRIORIDAD

Indica el tipo de prioridad del traslado.

| Código | Descripción                                   |
|:-------|:----------------------------------------------|
| 1     | Sin-prioridad=programado                    |
| 5     | Medio (NoUrgente NoProgramado)              |
| 8     | Urgente                                     |
| 10     | 10=Emergencia                                 |








