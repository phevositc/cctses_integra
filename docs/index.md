# Guía de Integración CCTSES

Control de versiones

| Version | Fecha      | Autor      | Descripcion |
|---------|------------|------------|-------------|
| 1.0     | 14/10/2021 | Phevos ITC | Versión 1.0 |
| 1.2     | 20/11/2021 | Phevos ITC | Versión 1.2 | 
| 1.3     | 03/04/2022 | Phevos ITC | Versión 1.3 |
| 1.4     | 05/04/2022 | Phevos ITC | Versión 1.4 |
| 1.5     | 15/10/2024 | Phevos ITC | [Versión 1.5](versions/1.5/index.md) |
| 1.6     | 10/11/2025 | Phevos ITC | [Versión 1.6](versions/1.6/index.md) |


## **1. Introducción**

El presente documento tiene como objetivo explicar la forma de hacer uso de la interfaz de integración entre la 
aplicación/software CCTSES y el software de la empresa concesionaria del servicio de transporte Sanitario (en 
adelante la Empresa) para poder así integrar ambos sistemas.

La integración se realizará a través de 2 servicios web, de tipo cliente-servidor, utilizando el estándar REST y 
JSON como formato para el intercambio de información.

Para distinguir estos 2 servicios-web, lo nombraremos con los siguientes nombres:

- **Circuito EMPRESA-CCTSES**:<br>
  Este servicio-web recibirá las peticiones enviadas desde el software de la Empresa al aplicativo de CCTSES..

- **Circuito CCTSES-EMPRESA**:<br>
  Este servicio-web enviará las peticiones enviadas desde la aplicación de CCTSES al software de la Empresa.


## **2. Entornos**


Para poder llevar a cabo la integración de forma exitosa, se necesita completar unas determinadas fases:

1. Fase de desarrollo (software de la Empresa)
2. Fase de pruebas en entorno de pruebas (Empresa y CCTSES)
3. Fase de pruebas en entorno de pre-producción (Empresa y CCTSES)
4. Puesta en producción

Para cada una de las fases de pruebas, es necesario disponer de un entorno para llevar a cabo las pruebas de integración.

> La fase en entorno de pruebas pueden no ser obligatorias si ambas partes estuvieran de acuerdo.

En cada fase de pruebas se utilizará lo que se denomina una *enviroment* o entorno, y para cada *environment* existirán una serie de configuraciones distintas, que será necesario aplicar.

En cada *environment*, cada parte de la integración (sistemas) tendrá una configuración software y hardware, que será independiente y no afectará a la misma, pero sí es necesario definir una serie de información que se utilizará para poder conectar con los sistemas.

**La comunicación se realizará cifrada a través de un túnel seguro entre el Origen y el Destino de la comunicación.**

### Configuraciones necesarias:

- *`{server}`*: indica la información del servidor. Dirección IP o DNS.
- *`{puerto}`*: indica el nº puerto a través del cual se va a realizar la comunicación.


En cada fase existirá una configuración específica de estos parámetros de conexión, y para cada circuito.

> En futuras versiones de este documento se irán incorporando las configuraciones para cada uno de los entornos.

Las configuraciones serán distintas para cada circuito.


## **3. Comunicación entre sistemas**

La comunicación entre los sistemas como se ha mencionado antes se realizará a través de una conexión segura a través de un túnel. La forma de llevar a cabo esta securización de la línea queda fuera del ámbito de este documento.



## **4. Circuitos**

Cada circuito es indipendiente y tendrá una operativa totalmente distinta.

Las operaciones disponibles en cada circuito están documentadas a través de su correspondiente documentación.

Esquema de ciruitos de integración

<figcaption>
  <img src="img/esqume-circuitos.png" width="100%" align="center">
  <figcaption align="center">Esquema de ciruitos de integración</figcaption>
</figcaption>


<br>
<br>


## 5. Documentación

La documentación de cada uno de los circuitos está dividida en sus diferentes versiones. Dentro de cada versión se encuentra la información de cada uno de los circuitos.

Las información de las tablas de referencia, con los código o valores que se utilizan para el intercambio unificado entre sistemas, se encuentra en el apartado "Tablas de referencia".

La información funcional de los aspectos técnicos específicos se encuentra en [Aspectos funcionales](./funcional-info.md).

Si hubiera alguna información funcional relevante solo para una determianda versión, se incluirá en un apartado específico dentro de esa versión.

**Versiones**

- [Versión 1.5](versions/1.5/index.md)
- [Versión 1.6](versions/1.6/index.md)





