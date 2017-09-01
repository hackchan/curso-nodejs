## Curso profesional de NODEJS

# Que es Nodejs

   Nodejs es una plataforma opensource
   para desarrollar aplicaciones RealTime,
   esta plataforma es similar JVM (Java Virtual Machine) o el framework .Net de microsoft.

   Ideal para Aplicaciones:
   
    * Alta Concurrencia
    * Aplicaciones en Red
   
   utiliza Javascript como lenguaje de programacion y gracias a esto nace el concepto de fullStack JS ya que se usa tanto para Backend y Frontend JavaScript.

   Nodejs es una plataforma simple para desarrollar:

   *  Network-centric (servidor web)
   *  modular
   *  JavaScript Aplicaciones
   *  Asincronismo, programacion        
      event-driven (orientados a eventos)

   La filosofia de Nodejs es mantener un core lo mas pequeño posible.

   ** Una libreria estandar es donde el codigo va a morir**

   ese pequeño core de Nodejs se complemente con el userlan(NPM)
   Node Pakage Manager.

###### Arquitectura NodeJS
``` 
 JS          NODEJS.JS CORE API
------------------------------------------
      |         NODE.JS BINDINGS         |
C/C++ | ---------------------------------|
      |     V8             OPENSSL       |
      | JavaScript  LIBUV  ZLIB          |
      |   Engine           HTTP_PARSER   |
      ------------------------------------
``` 
Gracias a V8 podemos usar javascript fuera del navegador y hacer el binding con C/C++.

La libreria LIBUV nos ayuda al manejo de event loop (Ejecucion de tareas asincronas), Operaciones de red y las operaciones de entrada y salida del sistema de archivo.

Mas de 1/4 de Nodejs esta dedicado al networking, modulos como
 * http
 * https
 * net (para crear servidores TCP)
 * degrant (para crear servidores UDP)
 * DNS

 NodeJs  es alatemente Modular y evita crear aplicaciones Monolitos.

 Monolito: son aquellas aplicaciones donde se intenta resolver todos los problemas.

###### Instalacion NodeJS
https://nodejs.org/es/

**NVM**
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash

###### Que se va a desarrollar
```                       
                             ON DEMAND
         --------|DB|<--------------------------
ON DEMAND|                                     | 
         |                                     | 
         v         PROXY         REAL TIME     |
     |API SERVER| <-----> |WEB|<----------|MQTT SERVER|
                                               ^
                   auth                        |  REAL TIME
                   jwt                         |
                                               v
                                          |ANY NODEJS APP| AGENTE

```
###### Que es PUBSUB
 
    PubSub es un patron de mensaeria:
    
    * En este modelo uno se escribre en un canal donde
      se van a enviar mensajes por ejemplo un CHAT, yo 
      solo voy a resivir informacion de los canales que 
      este suscrito.

    * Cualquier entidad que este conectada a la red y 
      que publique un mensaje a ese canal la red  podra 
      redistribuirlo a todos los usuarios que esten 
      suscritos a ese canal.

    yo como usuario de la red me puedo suscribir en un canal y tambien puedo publicar a este.

    hay protrocolos que manejan el patron pubsub como es
    MQTT que corre en el protocolo TCP/IP diseñado para conecciones limitadas bien sea por ancho de banda o tamaño del mensaje esto lo hace optimo para aplicaciones de IOT (internet de las cosas).

###### Que se WEBSOCKETS

    * Este es un protocolo full duplex esto quiere decir 
      que el cliente y el servidor van a tener un  canal 
      de comunicacion bidireccional.
    
    * la conexion se realiza sobre un unico canal TCP entre 
      el cliente y el servidor
    
    * para entablecer una comunicacion 
      de websokect debe haber un handshake entre el cliente y el 
      servidor este se hace a traves de htpp para hacer un upgrade 
      http a websocket de esta forma puede haber intercambio de 
      mensajes hasta que cualquiera de los dos lados decida cerrar 
      el canal.
###### Que Puedo programar con NODEJS

      * DesktopAPPS
      * Mobile Devices (sporte nativo NodeJS con React Native)
      * Web UI
      * API Service / Serveless
      * Embedded Devices
###### Instalacion ORM
       * sequelize (ORM)
       * pg (Driver Postgrest)
       * pg-hstore (requerida por sequelize)
       
       ```npm i sequelize pg pg-hstore --save```      
###### Definicion de entidades de base de datos
```
      DROP TABLE Agent;
      DROP TABLE Metric;

      CREATE TABLE Agent (
        id   int NOT NULL,
        uiid int NOT NULL,
        name     character varying NOT NULL,
        username character varying NOT NUll,
        pid  int NOT NULL,
        connected boolean NOT NULL,
        createAt  date NOT NULL,
        updateAt  date NOT NULL,
        CONSTRAINT Agent_id_PK PRIMARY KEY(id)
    );


     CREATE TABLE Metric (
        id         int NOT NULL,
        agentId    int NOT NULL,
        type       character varying NOT NULL,
        value      character varying NOT NUll,
        createAt   date NOT NULL,
        updateAt   date NOT NULL ,
        CONSTRAINT Metric_id_PK PRIMARY KEY(id),
        CONSTRAINT Metric_id_FK FOREIGN KEY(agentId) REFERENCES Agent(id)
    );
```

# Imagenes       
Las Imagenes se debe exportar al doble de resolucion a como las vamos a usar:
***Ejemplo***
uso: 
     width:45px
     height:45px

la exportamos desde cualquier herramienta grafica que se use 
( Photoshop cmd + alt + shift + s ). Width: 90px Height:90px ya 
con esto le damos soporte a pantallas con el doble de resolucion. 

# Llave publica
La llave publica nos es util para autenticarnos de manera seguro con algun servidor, en este caso la vamos a usar para autenticarnos con github.
```
ssh-keygen -t rsa -b 4096 -C "fabiorojas7@gmail.com" 
```
el .pub generado lo agregamos en settings / SSH and GPG keys
y damos click en new SSH key.

cuando bloqueamos un usuario por intentar un maximo de intentos permitidos:
ssh -o IdentitiesOnly=yes -i id_rsa root@ip

# License

```
Copyright 2017 FABIO ROJAS

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

```

# Autor
[FABIO ROJAS](https://twitter.com/#hackchan77)