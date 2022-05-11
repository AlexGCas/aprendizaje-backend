# Conceptos de backend
- ## Capas del modelo osi y protocolos de comunicación
    - referencias:
        - capas del modelo osi:
            - https://www.youtube.com/watch?v=7IS7gigunyI
            - https://www.youtube.com/watch?v=lUo45NqPyq8&list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW&index=5
            - https://www.youtube.com/watch?v=AtITX-U2mL4&list=PL1rFvQRVWVVaDtvhQxWa8eLVShDUTTbvQ&index=12
        - tcp y udp 
            - tcp vs udp: https://www.youtube.com/watch?v=qqRYkcta6IE
            - datagram: https://www.techopedia.com/definition/6766/datagram
    - ## TCP
        - la conexión se realiza utilizando 
    - UDP
    - Websockets: https://www.youtube.com/watch?v=2Nt-ZrNP22A&list=PLQnljOFTspQUGjfGdg8UvL3D_K9ACL6Qh&index=2 https://www.youtube.com/watch?v=1BfCnjr_Vjg
    - Bidirectional
    - grpc: https://www.youtube.com/watch?v=Yw4rkaTc0f8
- ## HTTP 1.0, 1.1, HTTP/2, HTTP/3
    - referencias: 
        - http 1.0, 1.1, 2 y 3: https://www.youtube.com/watch?v=0OrmKCB0UrQ
        - http 2: https://www.youtube.com/watch?v=fVKPrDrEwTI
        - tls: https://www.youtube.com/watch?v=AlE5X1NlHgg
        - https: https://www.youtube.com/watch?v=clK8Wf4-F5k
    - utiliza por defecto el puerto 80.
    - el protocólo http es stateless (ver sesion de stateless), el servidor no utiliza información de una request anterior para resolver la request actual.
    - el protocolo de transferencia de hipertexto es un protocolo de transferencia de datos de la capa de aplicación.
    - arquitectura cliente servidor: un cliente hace una petición (request) a un servidor y este devuelve una respuesta)
        - ejemplos de clientes: navegador, aplicaciones de python, javascript, postman, insomnia, curl, etc.
        - ## partes de una http request
            |parte|ejemplos|
            |------|-------|
            |url|https://es.wikipedia.org/|
            |metodo|GET, POST, PUT, DELETE|
            |headers|User-Agent, Accept, Accept-language, localization, proxy|
            |body|{username: Alex, password: 123}, contenido, etc|
        - ejemplos de servidor: nodejs, flask, etc, http web server como apache, etc.
        - ## partes de una http response
            |parte|ejemplos|
            |------|-------|
            |status code|200, 300, 400, 500|
            |headers|content-type, content-length, etc|
            |body|html, imagenes, etc|
    - ## HTTP 1.0
        - envía una sola parte de la página y cierra la conexión.
        - para enviar la página completa es necesario realizar múltiples conexiones.
        - la transferencia de la página se hace por pedazos y para cada pedazo hay qué hacer una nueva conexión.
    - ## http 1.1
        - implementa el header keep-alive para mantener la conexión hasta que la transferencia sea realizada.
        - la transferencia de la página se hace por pedazos y todos los pedazos se envían durante una misma conexión
        - si se necesitan varios archivos (ej: main.html, main.js, ...), se realiza una request para cada uno de esos archivos
        y por ejemplo la petición de main.js no se puede ejecutar hasta que se termina la petición de main.html (una petición a la vez, 1 conexión por archivo).
        - compresión de datos pero no de headers.
    - ## http 2
        - multiplexado: multiples request son realizadas por la misma conexión TCP (varios archivos pueden ser solicitados en una misma request), cada request tiene asociado un stream id para que el servidor identifique a qué request pertenece cada response. las request son procesadas una por una y se asigna un response id para que el client identifique a qué resquest pertenece cada response.
        - server push: el servidor puede ser configurado para enviar múltiples responses para una misma request (ej: si se solicita index.html es probable que también se requiera index.css, indexjs, etc de acuerdo a la lógica de la aplicación, así que se pueden enviar las response de todos estos archivos a la petición de index.html pero el cliente debe ser configurado para recibirlos) 
        - compresión de headers y datos.
        - implementa tls por defecto.
    - ## http 3
        - cambia TCP por QUIC (UDP + congestion control para mejorar un poco la confiabilidad de transmisión)
        - no se garantiza el envío en orden y completo por no usar TCP.

- ## partes de una url
    - ## referencias:
        - URI, URL, URN: https://www.youtube.com/watch?v=vpYct2npKD8

    |protocolo|separador|localizacion|puerto de recepción del cliente (opcional)|path|query|segmento|
    |---------|------|----|---|-|-|-|
    |https|://|es.wikipedia.org|:80|/Protocolo_de_transferencia_de_hipertexto||#mensaje|
- ## Stateful
    Una aplicación es stateful si la información del cliente es guardada en el servidor para futuras transacciones.
    <br>
    **Ventajas**:
        <ul>
            <li>
                El manejo de peticiónes es más rápido.
            </li>
        </ul>
    <br>
    **Desventajas**:
        <ul>
            <li>No es escalable, el servidor requiere guardar mucha más información en memoria y a medida que aumenta la cantidad de clientes aumenta cantidad de información que debe almacenar el servidor.</li>
            <li>
                Como el estado se encuentra en memoria, si un cliente intenta ingresar por otro servidor, este no tendra la información de su estado y no podrá acceder, igualmente si un servidor se cae toda la información de los estados de usuarios se caen y necesitan identificarse de nuevo en otro servidor.
            </li>
        </ul>
- ## Stateless
    La petición actual se ejecuta sin ser afectada por las peticiones anteriores que haya realizado el cliente.
    <br>
    **Ventajas**:
        <ul>
            <li>
                El manejo de peticiones es más predecible porque no depende de peticiones anteriores para resolver la petición actual.
            </li>
        </ul>
    <br>
    **Desventajas**:
        <ul>
            <li>
                El tamaño de paquete enviado al servidor es más grande porque hay qué enviar toda la información necesaria para manejar la petición cada vez que se hace una petición.
            </li>
        </ul>
- ## Rest:
    - ## referencias:
        - rest  hussein nasser: https://www.youtube.com/watch?v=EKCM1oQQrCM

    Representational "state transfer", el estado es ***representado*** mediante una ***transferencia de estado***. El servidor no guarda ninguna información sobre el cliente (es decir, ***stateless***), la ***transferencia de estado*** se encarga de enviar toda la información necesaria para identiicar el usuario y la petición se realiza exclusivamente con base al estado ***representado*** por la ***transferencia de estado***.
- ## Web servers
    - ## referencias:
        - web servers hussein nasser: https://www.youtube.com/watch?v=JhpUch6lWMw&list=PLQnljOFTspQUNnO4p00ua_C5mKTfldiYT&index=10
        
    un web server es un software que entrega contenido web, usa el protocolo http, puede entregar contenido estático o dinámico y se puede usar para servir APIs, páginas web y blogs.
    - ## static vs dynamic
        |static|dynamic|
        |------|-------|
        |el contenido está en archivos descargables y no es modificable.|el contenido es consultado a una base de datos y entregado al usuario.|
    - un web server responde a peticiones http.
    - ## blocking single-threaded web server:
        - el servidor reserva memoria para resolver la petición (tcp socket) que no puede ser utilizado en ninguna otra función hasta que la petición sea resuelta.
        - el tcp socket no puede ser utilizado para resolver peticiones de otros clientes, si un segundo cliente intenta acceder al servidor debe crearse otro tcp socket.
        - si un client intenta realizar una request mientras otro está haciendo su request, no se puede realizar hasta que el otro cliente termine la request (blocking single-threated)
        - ### ventajas:
            - asignar memoria a un client puede resultar rápido porque en las siguientes request irá directamente a la memoria asignada.
            - a pesar de que es single threaded, se pueden levantar varios servidores de este tipo para 
        - ### desventajas:
            - reservar memoria lo hace suceptible a ataques porque es fácil conectarse con varios client y que utilizen toda la memoria.
            - no se pueden resolver varias request simultaneamente en un servidor.
        - ## ejemplos de web servers:
            - httpd (de apache).
            - tomcat.
            - IIS.
    - Web server vs proxy: nginex
- ## Database engineering
- ## Proxy
    - Proxy
    - Reverse proxy
        - Caching layer
        - Load balancer
- ## Caching
    - Stateful vs stateless
    - Messaging systems
- ## Api web frameworks
- ## Message formats
    - Xml
    - Json
    - Yml
    - Protocol buffers
- ## Security
    - referencias:
        - Transport Layer Security, TLS 1.2 and 1.3: https://www.youtube.com/watch?v=AlE5X1NlHgg
        - Transport Layer Security (TLS) - Computerphile: https://www.youtube.com/watch?v=0TLDTodL7Lc
        - Secret Key Exchange (Diffie-Hellman) - Computerphile: https://www.youtube.com/watch?v=NmM9HA2MQGI
    
    - ## TLS, transport layer security:
        - 
    - ## https
        - utiliza por defecto el puerto 443.
        - client y server guardan una llave para encriptar y desencriptar la información enviada en la request y la response (encriptación simétrica).
        - utiliza tls para encriptar.

# referencias
- 5 conceptos que debe conocer un backend junior: https://www.youtube.com/watch?v=8fCPeivEJtE
- 100 computer science concepts: https://www.youtube.com/watch?v=-uleG_Vecis
- 50 amazon web services: https://www.youtube.com/watch?v=JIbIYCM48to
- 
- 
- stateless vs statefull hussein nasser: https://www.youtube.com/watch?v=nFPzI_Qg3FU
- sesion vs token: https://www.youtube.com/watch?v=UBUNrFtufWo
- json web token web simplified: https://www.youtube.com/watch?v=7Q17ubqLfaM
- javascript cookies vs local storage vs session: https://www.youtube.com/watch?v=GihQAC1I39Q
- web sockets hussein nasser: https://www.youtube.com/watch?v=2Nt-ZrNP22A
- backend overview: https://www.youtube.com/watch?v=XBu54nfzxAQ
- 5 cosas que hace un programador backend: https://www.youtube.com/watch?v=gkAEFL6AzOI&list=PLWYKfSbdsjJgEzDcvUet7dCNisJ9D98Pz
- how to become a good backend engineer: https://www.youtube.com/watch?v=V3ZPPPKEipA&list=PLQnljOFTspQUNnO4p00ua_C5mKTfldiYT&index=2
- system design fundamentals: https://www.youtube.com/watch?v=SqcXvc3ZmRU&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=8




