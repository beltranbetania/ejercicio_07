# README #

A continuación ejecuta este comando en una terminal: docker-compose -f docker-compose-jobvacancy.yml up.

* ¿Cuántos contenedores se están ejecutando?
    Se ejecutan 2 contenedores: 
    - ejercicio_07_web_1
    - ejercicio_07_db_1
* ¿Cuales son las imágenes en las que están basados los mencionados contenedores?
    - nicopaez/jobvacancy-ruby:1.3.0
    - postgres
* ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?
 
    - services: ---> a continuación se declaran los servicios
    - web: 
    -     image: nicopaez/jobvacancy-ruby:1.3.0 ---> inidica la inagen en la que se basa el contenedor
    -     links: ---> Crea enlace a un contenedor en otro servicio
    -     - db ---> Contenedor al que se enlaza 
    -     ports: ---> Indica el puerto o los que se va a compartir con los otros servicios
    -     - "3000:3000" 
    -     environment: ---> Se setean las variables de entorno del contenedor
    -     PORT: "3000"
    -     RACK_ENV: "production"
    -     DATABASE_URL:
    -     depends_on: ---> Expresa dependencia con el servicio db.
    -     - db
    - db:
    -     image: postgres ---> inidica la inagen en la que se basa el contenedor
    -     environment:  ---> Se setean las variables de entorno del contenedor
    -     POSTGRES_PASSWORD: 

* Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?
    - Es posible ya que los enlaces le permiten definir alias adicionales mediante los cuales se puede acceder a un servicio desde otro servicio