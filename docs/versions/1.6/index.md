# Guía de Integración CCTSES. Versión 1.6

**Actualizada a fecha: 17/11/2025.**

## **Cambios**


!!! tip "Circuito A (Empresa -> CCTSES)"

    Cambios respecto a la versión anterior

    **UnidadAdscrita**: Se utiliza en la nueva operativa de trabajo

    - Operacion `PUT /api/v1/unidad/principal`  (agregado)
    - Operacion `PUT /api/v1/unidad/secundario`  (agregado)


!!! info "Circuito B (CCTSES -> Empresa)"

    Cambios respecto a la versión anterior

    **Las planificaciones** ya no son requeridas por nueva operativa de trabajo.

    - Operacion `POST /api/v1/planificacion` (eliminada)
    - Operacion `PUT  /api/v1/planificacion` (eliminada)


    **PaqueteTraslado**: Se utiliza en la nueva operativa de trabajo

    -  Operacion `POST /api/v1/paquetetraslado`  (agregado)
    -  Operacion `PUT  /api/v1/paquetetraslado`  (agregado)


    **UnidadAdscrita**: Se utiliza en la nueva operativa de trabajo

    - Operacion `GET /api/v1/unidad`  (agregado)

    **Traslado. Pre-assignacion, asignacion y desasignacion**: Se utiliza en la nueva operativa de trabajo

    - Operacion `POST /api/v1/trasladoasignado`  (agregado)
    - Operacion `PUT  /api/v1/trasladoasignado/{idTrasladoCctses}/{idUnidad}`  (agregado)
    - Operacion `DELETE /api/v1/trasladoasignado/{idTrasladoCctses}`  (agregado)




## Documentación

Las información de las tablas de referencia, con los código o valores que se utilizan para el intercambio unificado entre sistemas, se encuentra en el apartado "Documentación funcional".

La información funcional de los aspectos técnicos específicos se encuentra en [Aspectos funcionales](../../funcional-info.md).

Si hubiera alguna información funcional relevante solo para una determianda versión, se incluirá en un apartado específico dentro de esa versión.


### Detalle por Circuito

- Circuito A: Empresa ➡️ CCTSES
    - [Documentación técnica](CircuitoA/circuitoA-doc.md)
    - [Documentación funcional](CircuitoA/CircuitoA-doc_funcional.md) 

- Circuito B: CCTSES ➡️ Empresa
    - [Documentación técnica](CircuitoB/CCTSES-doc_tecnica.md)
    - [Documentación funcional](CircuitoB/CircuitoB-doc_funcional.md)




## Información de Headers

Todas las peticiones de cualquier tipo (POST, PUT, DELETE, ...) requieren los siguientes headers:

| Header | Descripción | Ejemplo |
|:--|:--|:--|
| *x-request-id* | Identificador único de la petición. Formato: Fecha de la petición en formato: YYYYMMDDHHmmSS.sss | 20251107115368.2525 |
| *x-source* | Identificador del sistema que envia la petición. (Empresa, CCTSES) | Empresa |









