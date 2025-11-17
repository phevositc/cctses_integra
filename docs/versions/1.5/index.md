# Guía de Integración CCTSES. Versión 1.5


**Actualizada a fecha: 17/10/2024.**

## Cambios

(no disponible)


## Documentación

Las información de las tablas de referencia, con los código o valores que se utilizan para el intercambio unificado entre sistemas, se encuentra en el apartado "Documentación funcional".

La información funcional de los aspectos técnicos específicos se encuentra en [Aspectos funcionales](../../funcional-info.md).

Si hubiera alguna información funcional relevante solo para una determianda versión, se incluirá en un apartado específico dentro de esa versión.

### Detalle por circuito

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