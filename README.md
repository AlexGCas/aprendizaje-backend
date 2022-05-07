# Conceptos de backend
- ## Capas del modelo osi y protocolos de comunicación
    - TCP
    - UDP
    - Websockets: https://www.youtube.com/watch?v=2Nt-ZrNP22A
    - Bidirectional
    - grpc: https://www.youtube.com/watch?v=Yw4rkaTc0f8
- ## HTTP 1.0, 1.1, HTTP/2, HTTP/3
    el protocolo de transferencia de hipertexto es un protocolo de transferencia de datos de la capa de aplicación.
- ## partes de una url

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
- URI, URL, URN: https://www.youtube.com/watch?v=vpYct2npKD8
- rest  hussein nasser: https://www.youtube.com/watch?v=EKCM1oQQrCM
- stateless vs statefull hussein nasser: https://www.youtube.com/watch?v=nFPzI_Qg3FU
- sesion vs token: https://www.youtube.com/watch?v=UBUNrFtufWo
- json web token web simplified: https://www.youtube.com/watch?v=7Q17ubqLfaM
- javascript cookies vs local storage vs session: https://www.youtube.com/watch?v=GihQAC1I39Q
- HTTP 1.0, 1.1, HTTP/2, HTTP/3 https://www.youtube.com/watch?v=0OrmKCB0UrQ
- web sockets hussein nasser: https://www.youtube.com/watch?v=2Nt-ZrNP22A
- backend overview: https://www.youtube.com/watch?v=XBu54nfzxAQ
- 5 cosas que hace un programador backend: https://www.youtube.com/watch?v=gkAEFL6AzOI&list=PLWYKfSbdsjJgEzDcvUet7dCNisJ9D98Pz
- how to become a good backend engineer: https://www.youtube.com/watch?v=V3ZPPPKEipA&list=PLQnljOFTspQUNnO4p00ua_C5mKTfldiYT&index=2
- system design fundamentals: https://www.youtube.com/watch?v=SqcXvc3ZmRU&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX&index=8