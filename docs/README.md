---
layout: page
title: Instalacion
permalink: /instalacion/
hero_height: is-fullwidth
---
## Dependencias a otros modulos:
- base

- contacts
    - res.partner
    - res.country
    - res.country.state

- hr
    - hr.employee

## Dependencias externas:
- Geopy

## Preparación del sistema:
- Desde cero.(Si tienes instalado un odoodock lee el siguiente punto.)
    1. Es conveniente crear en local una carpeta llamada Odoo_dev o [nombre de la
        empresa]_dev.
        ```shell
        mkdir odoo_dev
        ```
    2. Clonar en su interior odoodock.
        ```shell
        cd odoo_dev
        git clone https://github.com/JosemaVlc/odoodock.git
        ```
    3. Copiar ficheros .env-example a .env y .services-example a .services.
        ```shell
        cd odoodock
        cp .env-example .env
        cp .services-example .services
        ```
    4. Asignar permisos de ejecución para el usuario al fichero up.sh y create-module.sh.
        ```shell
        chmod u+x ./up.sh
        chmod u+x ./create-module.sh
        ```
    5. Arrancar los servicios.
        ```shell
        ./up.sh
        ```
        Puedes comprobar que los contenidos estan en ejecución con:
        ```shell
        docker compose ps
        ```
        tambien puedes comprobarlo con:
        ```shell
        docker ps
        ```
    6. Para comprobar que todo ha ido correctamente, acceder desde un navegador a localhost:8069, donde debe aparecer la página del selector de la base de datos.
    ![Imagen con pantalla de creacion de la base de datos](./img/odoo_base_datos.jpg)

    7. Configurar los valores y crea la base de datos.

    8. En la termina accede al servicio web
        ```shell
        docker exec -it odoodock-web-1 bash
        ```
    9. Clona el modulo de incidencias en la carpeta extra-addons.
        ```shell
        cd /mnt/extra-addons
        git clone https://github.com/JosemaVlc/incidencias.git
        ```
- Utilizando un odoodock ya instalado.(Si tienes no tienes odoodock instalado haz la instalación desde cero.)
    1. Arranca los servicios.
    2. Entra en el servicio web.
        ```shell
        docker exec -it [nombre de tu servicio web] bash
        ```
    3. Instala geopy.
        ```shell
        pip3 install geopy
        ```
    4. Localiza tu carpeta extra-addons, y una vez dentro, clona el modulo incidencias
        ```shell
        cd /mnt/extra-addons
        git clone https://github.com/JosemaVlc/odoodock.git
        ```
    5. Logueate en localhost y activa modo desarrollador
    6. Recuerda tener instalado los modulos contactos y empleados, si no es así instalalos.
    7. Instala el modulo incidencias

## Información para el buen funcionamiento.
- Para que funcione correctamente el modulo, debemos tener en el modulo de empleados(hr) un departamento con el nombre "Tecnico" esto es necesario para que se puedan asociar los empleados de ese departamento a las zonas correspondientes.
- Para que se asocie correctamente un contrato a una zona, es necesario, que el contacto asociado tenga codigo postal y pais, ya que sinó no se asociará a ninguna zona y no podrá guardar el contrato.

# Información de permisos.
- El modulo de incidencias dispone de una categoria de permisos llamada Incidencias que a su vez dispone de cuatro perfiles con diferentes tipos de permisos.

    * Direccion de empresa
        * Permisos de lectura sobre los contratos.
        * Permisos de lectura y modificacion sobre las incidencias.
        * Permisos de lectura y creacion sobre las anotaciones.
        * Permisos de lectura sobre las zonas.
        * Permisos de lectura sobre los almacenes.
        * Permisos de lectura sobre los materiales.
        * Permisos de lectura sobre las lineas de los albaranes de consumo.
        * Permisos de lectura sobre los albaranes de consumo.

    * Encargados de Departamento
        * Permisos totales sobre los contratos.
        * Permisos totales sobre las incidencias.
        * Permisos totales sobre las anotaciones.
        * Permisos totales sobre las zonas.
        * Permisos totales sobre los almacenes.
        * Permisos totales sobre los materiales.
        * Permisos totales sobre las lineas de los albaranes de consumo.
        * Permisos totales sobre los albaranes de consumo.

    * Tecnico Integrado
        * Permisos de lectura sobre los contratos.
        * Permisos de lectura y modificación sobre las incidencias.
        * Permisos de lectura y creacion sobre las anotaciones.
        * Permisos de lectura sobre las zonas
        * Permisos de lectura sobre almacén.
        * Permisos de lectura y modificación sobre material.
        * Permisos de lectura y creación sobre las lineas de los albaranes de consumo.
        * Permisos de lectura y creación sobre los albaranes de consumo.

    * Atencion al cliente y Comercial
        * Permisos de lectura, modificación y creación sobre contratos.
        * Permisos de lectura y modificación sobre incidencias.
        * Permisos de lectura y creación sobre anotaciones.
        * Permisos de lectura y modificación sobre zonas.
        * Permisos de lectura sobre almacenes.
        * Permisos de lectura sobre materiales.
        * Permisos de lectura sobre lineas de albaranes de consumo.
        * Permisos de lectura sobre los albaranes de consumo.

## URL del repositorios:
- [Repositorio del fork de odoodock](https://github.com/JosemaVlc/odoodock.git)
- [Repositorio del modulo](https://github.com/JosemaVlc/modulo_incidencias)
