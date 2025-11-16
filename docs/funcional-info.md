# Requerimientos funcionales

Además de los datos a intercambiar entre los sistemas, es necesario que además se cumplan una serie de requerimientos.

Estos requerimientos están basados en las funciones del CCTSES.

!!! info "Funciones del CCTSES"

    - Interlocución, coordinación y seguimiento de los asuntos que afectan al transporte sanitario.
    - Análisis de la prestación del servicio mediante el estudio de las reclamaciones planteadas, así como de las incidencias ocurridas en el mismo.
    - Seguimiento y control de las rutas, tiempos de respuesta y tiempos estimados de desplazamiento.
    - Acuerdos para el establecimiento de soluciones a los problemas surgidos en la prestación del servicio.
    - Emisión de cuantos informes le sean requeridos por el órgano contratante al respecto del transporte sanitario en su Área de Salud.
    - Información de las eventualidades que afecten al normal funcionamiento y/o calidad del servicio, así como incumplimiento de las cláusulas del contrato, a la Unidad de Seguimiento y Control de Transporte Sanitario del SES, dependiente de la Subdirección de AP.
    - Conocimiento de cualquier otra actividad relacionada con este servicio.
    - Apoyo al RCA (Reponsable de área) en actuaciones de supervisión, ejecución de decisiones e instrucciones de dicha Unidad.


Son también otras funciones las siguientes:

- Analizar y evaluar los informes de la empresa adjudicataria sobre la ejecución de las actuaciones realizadas, incidencias, tiempos de respuesta, reclamaciones de pacientes, etc.
- Conocer y evaluar los informes emitidos por los Responsables de Transporte Sanitario de cada una de las Áreas de Salud, sobre la prestación de los servicios y su adecuación a las condiciones previstas en el contrato.
- Realizar el seguimiento de la calidad de todos los servicios objeto del contrato.
- Proponer mejoras en los sistemas de gestión y control de la actividad.
- Ordenar la realización de los controles de calidad que se consideren necesarios con el fin de garantizar la adecuada prestación sanitaria y calidad asistencial.
- Dirimir las discrepancias que puedan surgir entre las empresas y las gerencias de Áreas de Salud.
- Comunicar al órgano contrato, mediante emisión del correspondiente informe:
    - Las deficiencias detectadas y las medidas propuestas y/o puestas en marcha para solventarlas.
    - Las propuestas de modificación de las condiciones de la prestación del servicio que impliquen alguna modificación de las cláusulas del contrato.
    - Emitir, a requerimiento del órgano contratante, los informes que éste determine pertinentes.
    - Cuantas funciones adicionales determine el responsable del contrato del SES.

**En base a esto se derivan una serie de requerimientos:**


### **Frecuencia de envio de status**

La monitorización del sistema es una parte fundamental de la integración, y es una de las funciones más importantes del CCTSES.

Por esto motivo, el envio de cada uno de los `status` es una parte vital del sistema/integración.

> El concepto **tiempo-real** implica que los `status` deben ser enviados tan pronto se generán.

!!! warning "Frecuencia envio de Status"

    Como norma general los `status` se deben enviar con un retraso **máximo de 2 minutos** desde su generación o creación.<br>
    Esta norma queda anulada, cuando exista una normativa específica para ese tipo de `status`.


!!! info "Frecuencia de envio de status"

    - `Status VEHICULO-ESTADO`: Aplica norma tiempo-real.
    - `Status VEHICULO-MODOS` : Aplica norma tiempo-real.
    - `Status TRASLADO`: Aplica norma tiempo-real.
    - `Status JORNADA`: Aplica norma tiempo-real.
    - `Status VEHICULO-POSICIONAMIENTO`

        La normativa aplicable a este tipo de `status` es la siguiente:
        
        - Dentro de población como máximo con intervalo de un 2 minuto.
        - Fuera de población como máximo con intervalo de cada 4 minutos.
        
        > *Preferentemente la frencuencia de envio será cada mínuto, tanto en urbano como interurbano.*


### **Información de trazabilidad**

La trazabilidad de los datos implica que se pueda identificar a qué sistema o recurso pertenece cada uno de los datos, y evolución en el tiempo.

De los datos enviados desde la Empresa concesionaria se realizará un historial de trazabilidad, de todos los recursos de los que se envía información.

> De toda esta información se obtendrán tantos informes, gráficos o inferencia de datos como sea necesario para la revisión de la concesión.




