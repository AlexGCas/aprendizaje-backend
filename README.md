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
    - Websockets: https://www.youtube.com/watch?v=2Nt-ZrNP22A&list=PLQnljOFTspQUGjfGdg8UvL3D_K9ACL6Qh&index=2
    - Bidirectional
    - grpc: https://www.youtube.com/watch?v=Yw4rkaTc0f8
- ## HTTP 1.0, 1.1, HTTP/2, HTTP/3
    - referencias: https://www.youtube.com/watch?v=0OrmKCB0UrQ
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
    - ## http 2
        - multiplexado: multiples request que pasan por un único canal.
        - comresión
        - server push: el client no tiene qué esperar a que llegue la response, el server la envía por si mismo cuando esté lista.
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
    - Static vs dinamic
    - Single threated vs multithreated
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
    -
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



git commit -m "algunos cambios de orden, se profundizo el tema de http, y se cambió la forma de referenciar"
