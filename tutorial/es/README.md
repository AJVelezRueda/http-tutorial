# Tutorial WEB
[Contenido del recorrido](#1-Web)
  * [1. Internet](#1-interntet)
  * [2. La Web](#2-web)
  * [3. Introducción al concepto de CLoud Computing](#3-Cloud-computing)
  * [4. Protocolos de comunicación](#4-protocolos)

[1. Internet](#1-interntet)

Internet se podría definir como la red de redes de computadoras, conectadas por medio de un cableado físico que permite intercambiar información entre todos sus usuarios. 

Para acceder al servicio que ofrece la información, debemos tener dos programas que se ejecutan en dos computadoras diferentes y que nos permiten compartir recursos. 

A la computadora que ejecuta el programa que proporciona el recurso o información se la denomina **servidor** y a la computadora que consume un recurso o información se la denomina **cliente**. En la computadora del cliente se ejecutará entonces el programa que le permite utilizar el recurso o leer la información.

Pero ¿Qué tipo de recursos pueden brindarse o consimirse a través de internet? Por medio de Internet podemos enviar mensajes, programas ejecutables, archivos de texto, consultar bases de datos, etc.

[2. La Web](#2-web)
La Web en particular, diminutivo de World Wide Web, es un conjunto de páginas interconectadas por las cuales podemos navegar.

Estas páginas web están pensadas para consumir contenido hipertextual, es decir  contenido que contiene vínculos o enlaces a otros contenidos.

[3. Introducción al concepto de CLoud Computing](#2-Cloud-computing)

La computación en la nube o Cloud Computing es el consumo o prestación bajo demanda de recursos tecnologicos a través de Internet. 

En lugar de comprar y mantener servidores y centros de datos físicos(es decir una super duper máquina en tu casa), podés consumir los servicios tecnológicos, como potencia informática, almacenamiento y bases de datos, según te sea necesario, en el momento que te sea necesario, de un proveedor.

[4. Protocolos de comunicación](#4-protocolos)

¿Alguna vez te preguntaste cómo es que logramos comunicarnos los seres humanos? ¿Cómo es que las palabras pueden estructurarse en conversaciones ordenadas? Bueno tal y como explica el Dr. Juan Eduardo Bonnin, <a href="https://www.youtube.com/watch?v=jrA70HwWnts&t=9s">en su video</a>, los seres humanos somos capaces de estructurar las palabras, y estas en oraciones que devienen en conversaciones. En este proceso se pone en juego no solo cuestiones ficiológicas, sino también cuestiones culturales y personales, como: la lengua, las normas sociales, los valores culturales, los intereses y propósitos individuales. Por tanto, lo que pensamos como un simple intercambio de palabras, se convierte en una actividad compleja, matizada con el ritmo de todo esta información extra...o meta 😝

Los protocolos, como verás, forman parte de nuestras vidas más de lo que pensábamos. Y estos pueden variar según el entorno en el que nos movemos. Cada ámbito posee sus propias reglas para la comunicación. No nos expresamos de igual modo cuando estamos en un recital, que cuando estamos en la facultad ¿No? 🙏

Este conjunto de reglas de comunicación, implícitas o explícitas, se denomina protocolo y en Internet hay uno específico para establecer la comunicación entre servidores y clientes. Este protocolo fue creado para la transferencia de archivos hipertextuales y se llama justamente HTTP, por las siglas en inglés de protocolo de transferencia de hipertexto (HyperText Transfer Protocol).


👇🏽 Vamos a ver un poco de qué se trata


# Tutorial HTTP
- [Tutorial HTTP](#tutorial--http)
  * [1. Primeros pedidos](#1-primeros-pedidos)
  * [2. Códigos de respuesta](#2-codigos-de-respuesta)
  * [3. Parámetros](#3-parametros)
  * [4. URLs y URIs](#6-urls-y-uris)
  * [5. Resolución de dominios](#7-resolucion-de-dominios)
  * [6. Cabeceras](#8-cabeceras)
  * [7. Borrando contenido](#11-borrando-contenido)
  * [8. Creando y actualizando contenido](#12-creando-y-actualizando-contenido)
  * [9. Sobre la semántica de los verbos](#13-sobre-la-semantica-de-los-verbos)
  * [10. Recursos](#14-recursos)
  * [11. Paréntesis: servidores y despliegue](#15-parentesis-servidores-y-despliegue)

> 🏁 Antes de empezar, repasemos: ¿qué es una arquitectura cliente-servidor? ¿cómo funciona? ¿Cuál es el cliente por antomasia de la Web?
>
> 🤔 Para pensar: ¿qué tecnologías se usan en la Web? ¿En qué se desarrolla un cliente? ¿Y un servidor?
>
>📚 Para indagar antes de empezar: ¿Cuál es la diferencia entre un sitio Web y una API web?

## 1. Primeros pedidos

Cada recurso de la web es localizable gracias a un identificador unívoco llamado URL, por las siglas en inglés de Localizador Uniforme de Recurso (Uniform Resource Locator). Las URL nos dan tanto la ubicación de un recurso como la manera de conseguirlo. 

> 🤔 Para pensar: ¿a qué corresponde cada parte de una URL? 

Para empezar, intentemos establecer nuestra primera comunicación con un servidor, para romper el hielo de esta conversación 🤣


Vamos a hacer nuestro primer pedido, para ello usaremos la biblioteca <a href="https://2.python-requests.org/es/latest/user/quickstart.html">**requests**</a> de Python. Podes instalarala haciendo:


```bash
$ pip install requests

```

Luego desde el intérprete de python podremos hacer finalmente nuestro primer pedido:


```python
>>> import requests
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas/1')
>>> r.json()
{
  "id": 1,
  "tipo": "pantalon",
  "talle": 35
}
```

Veremos que lo que nos devuelve no es HTML, sino un formato llamado JSON.  

>
>📚 Para indagar: ¿Sabés qué es HTML? Si aún no conoces este tipo de lenguaje hacé Ctr+u y observalo _in situ_
>
> 🤔 Para pensar: ¿Qué características tiene este formato? ¿Qué tipo de datos puede soportar? ¿por qué devolver JSON? ¿Quién puede leerlo? ¿A quién le sirve?


¡Ahora te toca a vos¡

>🏅 DESAFIO I: Hacé otro pedido para traer a la prenda `20`. Deberías obtener el siguiente resultado:

```bash
{
  "id": 20,
  "tipo": "saco",
  "talle": "XL"
}
```

## 2. Códigos de respuesta

 ¿Cuántas prendas existirán? ¿Existirá la prenda 400?

> 🏅 Desafío II: ¡averigualo! Hacé `requests.get('https://macowins-server.herokuapp.com/prendas/400')` y observá qué sucede.

<details>
  <summary>Respuesta</summary>

```python
  >>> import requests
  >>> r = requests.get('https://macowins-server.herokuapp.com/prendas/400')
  >>> r.json()
```
</details>

¡Momento! ¿Será un error? ¿Habrá forma de saberlo a ciencia cierta?

```python
>>> r.headers

{'Server': 'Cowboy', 
'Connection': 'keep-alive', 
'X-Powered-By': 'Express', 
'Expires': '-1', 
'Content-Type': 'text/html; charset=utf-8', 
'Content-Length': '0',
'Etag': 'W/"0-2jmj7l5rSw0yVb/vlWAYkK/YBwk"', 
'Vary': 'Accept-Encoding',
'Date': 'Sat, 27 Feb 2021 19:14:21 GMT', 
'Via': '1.1 vegur'}
```

Como dijimos antes, una conversación no se trata de la simple enunciación de palabras al azar. Existe un intercambio regulado o normado, donde es de esperar una estructura simple de enunciaciones/preguntas y respuestas. 

> En este caso ¿de qué tipo de respuesta se trata? Si tuvieras que expresarlo en emojis ¿Qué emoji es el 400?

> ✍️ Autoevaluación: ¿Para qué sirve el método `headers`? ¿Que nos permitió? 

> 🏅 Desafío III: contrastá con lo que sucede al hacer get de `'https://macowins-server.herokuapp.com/prendas/1'` ¿Qué te devuelve el método headers? 

<details>
  <summary>Respuesta</summary>

```python
  >>> import requests
  >>> r = requests.get('https://macowins-server.herokuapp.com/prendas/400')
  >>> r.headers

{'Server': 'Cowboy', 
'Connection': 'keep-alive', 
'X-Powered-By': 'Express', 
'Expires': '-1', 
'Content-Type': 'application/json; charset=utf-8', 
'Content-Length': '50', 
'Etag': 'W/"32-i8e+gZ5GUBVXp/2hTq5pj1i9+f8"', 
'Vary': 'Accept-Encoding', 'Date': 'Sat, 27 Feb 2021 18:11:12 GMT',
'Via': '1.1 vegur'}
```
</details>

> 🤔 Para pensar: ¿Qué cambió? ¿Qué cambio o cambios te parecen relevates entre ambas respuestas? ¿Qué emoji le pondrías a esta respuesta?

> 🏅 Desafío IV: ¿y que sucederá si consultamos a una dirección que no existe, como por ejemplo `https://macowins-server.herokuapp.com/prindas/1`? ¡Averigualo!

<details>
  <summary>Respuesta</summary>

```python
  >>> import requests
  >>> r = requests.get('https://macowins-server.herokuapp.com/prindas/1')
  >>> r.headers
HTTP/1.1 404 Not Found
....
```
</details>

`404` y `200` son códigos de estado (_status code_, también llamados a veces _códigos de respuesta_) y forman parte de toda respuesta HTTP.

> ✍️ Autoevaluación: ¿qué es un status code y para qué me sirve? 

Veamos otro código de respuesta más, que nos permitirá usar una funcionalidad que es _muy muy nueva y que quizás aún no ande bien_:

```bash
>>> r = requests.get('https://macowins-server.herokuapp.com/nueva-funcionalidad-que-a-veces-no-anda-bien')
>>> r.headers

{'Server': 'Cowboy', 
'Connection': 'keep-alive',
 'X-Powered-By': 'Express', 
 'Vary': 'Origin, Accept-Encoding', 
 'Access-Control-Allow-Credentials': 'true', 
 'Cache-Control': 'no-cache', 
 'Pragma': 'no-cache', 
 'Expires': '-1', 
 'Content-Security-Policy': "default-src 'none'", 
 'X-Content-Type-Options': 'nosniff',
 'Content-Type': 'text/html; charset=utf-8', 
 'Content-Length': '148', 
 'Date': 'Mon, 01 Mar 2021 20:18:38 GMT', 
 'Via': '1.1 vegur'}

>>> r.content
b'<!DOCTYPE html>
  <html lang="en">
      <head>
      <meta charset="utf-8">
        <title>Error</title>
      </head>
      <body>
        <pre>Internal Server Error</pre>
      </body>
  </html>'
```

¡Ups! 🙈

> ✍️ Autoevaluación: ¿qué representa el código `500`? ¿Por qué tenemos que hacer _r.contents_ además de _r.headers_? ¿Qué partes puede tener un mensaje HTTP? ¿Qué partes deben estar presentes y cuáles no? ¿En qué casos?


## 3. Parámetros

Hagamos un nuevo pedido, pero ahora a una _ruta_ ligeramente diferente:

```python
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas')
>>> r.json()
[
  {
    "id": 1,
    "tipo": "pantalon",
    "talle": 35
  },
  {
    "id": 2,
    "tipo": "pantalon",
    "talle": 36
  },
  {
    "id": 3,
    "tipo": "pantalon",
    "talle": 37
  },
  {
    "id": 4,
    "tipo": "pantalon",
    "talle": 38
  },
  ...
  {
    "id": 18,
    "tipo": "saco",
    "talle": "M"
  },
  {
    "id": 19,
    "tipo": "saco",
    "talle": "L"
  },
  {
    "id": 20,
    "tipo": "saco",
    "talle": "XL"
  }
]
```

> 🤔 Para pensar: ¿es lo mismo consultar `/prendas/` que `/prendas/1`? ¿En qué se diferencian? ¿Qué ocurre si hacemos _r.content_? ¿Por qué?

> 🤔 Para pensar: ¿qué hará `/ventas/2`? ¿`/ventas/`?.

> 🏅 Desafío V: hacé `requests.get('https://macowins-server.herokuapp.com/ventas')` y `requests.get('https://macowins-server.herokuapp.com/ventas/2)'` y contrastá el resultado con tu respuesta anterior

Este listado es muy completo, pero por eso también puede ser engorroso para usar. Quizás podríamos traer sólo una parte así...

```python
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas?tipo=pantalon')
>>> r.json()
[
  {
    "id": 1,
    "tipo": "pantalon",
    "talle": 35
  },
  {
    "id": 2,
    "tipo": "pantalon",
    "talle": 36
  },
  ....
  {
    "id": 10,
    "tipo": "pantalon",
    "talle": 44
  }
]
```

...o así:

```python
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas?tipo=saco')
[
  {
    "id": 16,
    "tipo": "saco",
    "talle": "XS"
  },
  {
    "id": 17,
    "tipo": "saco",
    "talle": "S"
  },
  {
    "id": 18,
    "tipo": "saco",
    "talle": "M"
  },
  {
    "id": 19,
    "tipo": "saco",
    "talle": "L"
  },
  {
    "id": 20,
    "tipo": "saco",
    "talle": "XL"
  }
]
```

> ✍️ Autoevaluación: ¿qué acabamos de hacer? ¿para qué nos sirvió el `?...=...`?

> 🏅 Desafío VI: Obtené las remeras.

Es común que las APIs que admiten parámetros soporten más de uno, por ejemplo:

```python
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas?talle=40')
[
  {
    "id": 6,
    "tipo": "pantalon",
    "talle": 40
  }
]
```

Además, los parámetros además se pueden combinar, utilizando el signo `&` (se llama _et_, aunque en informática es más común escucharlo por su nombre en inglés _ampersand_)

```python
>>> r = requests.get('https://macowins-server.herokuapp.com/prendas?talle=40&tipo=pantalon')
>>> r.json()
[
  {
    "id": 6,
    "tipo": "pantalon",
    "talle": 40
  }
]
```

> 🏅 Desafío VII: Obtené las remeras XS

> ✍️ Autoevaluación: ¿Para qué sirven los parámetros?


## 4. URLs y URIs

Pero ¿qué es `https://macowins-server.herokuapp.com/ventas/?_page=3`? Informalmente le diremos dirección, aunque su nombre técnico es URL.

¿Y qué es una URL? Es cualquier _string_ con un formato particular llamado _URI_ nos permita _localizar un recurso_, por ejemplo en internet.

Las URIs se componente de:

  * un protocolo
  * un dominio
  * opcionalmente, un puerto
  * una ruta
  * opcionalmente, parámetros
  * opcionalmente, un fragmento, que indica en que sección queremos obtener del recurso que estamos consultando.

Y se ven así: `protocolo://dominio:puerto/ruta#fragmento?parametro1=valor1&parametro2=valor2`. Las URIs son simplemente un formato estandarizado de strings,que por sí mismo no significa nada. Por ejemplo `cerebro://recuerdos:3403/recientes#hoy?tema=http` es sólo un string que cumple la estructura de una URI, aunque probablemente
no sea muy util (o al menos no el año 2020 🧠)

> 🏅 Desafío VIII: decí usando tus palabras qué significa la URI de este ejemplo _cerebral_ 😛.

> 🤔 Para pensar: ¿cuál es el protocolo que estamos estudiando? ¿Se observa en las URLs que venimos mencionando?

> ✍️ Autoevaluación: ¿es el string _tutoriales://http/introductorio#7_ una URI? ¿Y una URL?


## 5. Resolución de dominios

> 🤔 Para pensar: ¿Qué ocurrirá si hacemos un pedido a un dominio inexistente? ¿Qué código de estado HTTP obtendremos?

Observemos los siguientes pedidos:

```python
requests.get('http://localhost:300')
raise ConnectionError(e, request=request)
requests.exceptions.ConnectionError: HTTPConnectionPool(host='localhost', port=300): Max retries exceeded with url: / (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x7fb528ea62e8>: Failed to establish a new connection: [Errno 111] Connection refused',))
```

```python
>>> requests.get('http://unSitioQueProbablementeNoExistaEnInternet')
raise ConnectionError(e, request=request)
requests.exceptions.ConnectionError: HTTPConnectionPool(host='unsitioqueprobablementenoexistaeninternet', port=80): Max retries exceeded with url: / (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x7fb528e84a90>: Failed to establish a new connection: [Errno -2] Name or service not known',))

```

```python
>>> requests.get('http://google.com:8902',timeout=5)
    raise ConnectionError(e, request=request)
requests.exceptions.ConnectionError: HTTPConnectionPool(host='google.com', port=8902): Max retries exceeded with url: / (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x7fb5297f3cc0>: Failed to establish a new connection: [Errno 101] Network is unreachable',))
```

¡Ups! En un caso no pudo resolver el dominio, y en el otro, no había nada escuchando en el puerto.

> ✍️ Autoevaluación: ¿Por qué ante problemas de conexión obtenemos errores que no son de HTTP, sino de más bajo nivel?

> ✍️ Autoevaluación: ¿Para qué sirve el parámetro `timeout`? 


Como se puede ver, los pedidos antes hechos abre una serie de nuevos errores: errores de conexión, que como vemos pueden deberse, por ejemplo, a que el puerto al que estamos intentando conectarnos no es el adecuado o que el dominio no existe en internet.


> 💬 Para discutir: Pero, ¿qué es un dominio? ¿Qué otra forma tenemos de llegar a una máquina que sea a través de su dominio?

```Python
>>> import os
>>> hostname = "google.com"
>>> response = os.system("ping -c 1 " + hostname)
PING google.com (172.217.172.110) 56(84) bytes of data.
PING google.com (172.217.172.110) 56(84) bytes of data.
64 bytes from eze06s02-in-f14.1e100.net (172.217.172.110): icmp_seq=1 ttl=116 time=12.8 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 12.843/12.843/12.843/0.000 ms
```

> 🤔 Para pensar: ¿por qué Google tiene múltiples IPs? ¿Que ventaja representa para esta empresa y para quienes lo usamos?

> 🏅 Desafío IX: ¿a través de qué IP accedés a google desde tu computadora?

## 6. Cabeceras
Ya estuvimos analizando las partes de un pedido HTTP, ampliemos un poco sobre las cabeceras. Veamos un ejemplo:

```
HTTP/1.1 200 OK
X-Powered-By: Express
Vary: Origin, Accept-Encoding
Access-Control-Allow-Credentials: true
Cache-Control: no-cache
Pragma: no-cache
Expires: -1
X-Total-Count: 100
Access-Control-Expose-Headers: X-Total-Count, Link
Link: <https://macowins-server.herokuapp.com/posts/?_page=1>; rel="first", <https://macowins-server.herokuapp.com/posts/?_page=2>; rel="next", <https://macowins-server.herokuapp.com/posts/?_page=10>; rel="last"
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
Content-Length: 794
ETag: W/"31a-kfX25hKekB1DHqT0GE68BdzBP1Q"
Date: Sun, 19 Apr 2020 20:18:21 GMT
Connection: keep-alive
```

> 📝 Nota: si bien en requests 'se muestra de esta mantera (que a su vez tiene que ver con cómo funciona HTTP internamente), la primera línea NO se corresponde con una cabecera, sino que es el código de estado del que ya hemos hablado anteriormente.

Algunas de estas no las entenderemos. Pero las que sí nos dan información relevante:

* `X-Powered-By: QUIEN`: nos dice que software es el que está corriendo en el servidor. No siempre es muy confiable
* `Content-Length: TAMAÑO`: nos dice el tamaño de la respuesta
* `Date: FECHA`: nos dice la fecha en que se generó la respuesta
* `Content-Type: TIPO`: nos dice el tipo de contenido que estamos recibiendo, el cual podría ser, por ejemplo:
  * sonido, como `audio/wav`o `audio/ogg`
  * video, como `video/ogg`
  * una imagen, como `image/jpeg` o `image/gif`
  * un XML `application/xml`
  * un archivo css `text/css`

> 🤔 Para pensar: ¿Cuál fue el `Content-Type` de las respuesta del ejemplo? ¿Por qué devolvió eso?

> 🏅 Desafío X: ¿Qué devolverá la página principal (_home_) de nuestro sitio? Averiguá el `Content-Type` de /home

> ✍️ Autoevaluación: ¿Para qué sirven las cabeceras? Mencioná al menos dos.

## 7. Desde el navegador

¡Probemos estas mismas ideas desde el navegador!

> 🏅 Desafío XI: consultá 4 sitios diferentes y averiguá para todos ellos qué servidor utilizan,
> si el contenido se transfiere encriptado, y la fecha de expieración del contenido.

## 8. Borrando contenido

> ✍️ Autoevaluación: ¿qué es un método HTTP?

> 🤔 Para pensar: ¿es correcto que permitamos que cualquiera borre contenido?

> 🤔 Para pensar: Estuvimos usando un método específico de request GET, que servía para... ¿Para qué servía? ¿Qué crees que hará DELETE?

> 🤔 Para pensar: ¿Habrá algo que impida que no borre nada con un DELETE, o que borre algo con un GET?


## 9. Creando y actualizando contenido

Ahora probemos crear una prenda... para esto es lógico pensar que cierta información debe ser enviada al servidor ¿Pero, qué información? Bueno, probemos mandando un número identificador (id):

```Python
>>> data = {'id': 21}
>>>  r = requests.post('https://macowins-server.herokuapp.com/prendas/', data=data)
```

Podemos ver que se creó una prenda con el id `21`, si verificamos la respuesta del _recurso_ creado.

> 🏅 Desafío XII: ¿qué código de estado devuelve cuando un _recurso_ es creado? Averigualo

> 🤔 Para pensar: ¿Nos es realmente útil crear una prenda sin especificar más nada?

> 🤔 Para pensar: ¿Por qué se creó con el id `21`?

Pero para que las cosas sean más interesantes, vamos a especificar _el cuerpo_ del pedido HTTP, con el contenido de la prenda que queremos crear.

```python
>>> data =  { "tipo": "chomba", "talle": "XS" }
>>>  r = requests.post('https://macowins-server.herokuapp.com/prendas', data=data)

{
  "{ \"tipo\": \"chomba\", \"talle\": \"XS\" }": "",
  "id": 22
}
```

> ✍️ Autoevaluación: ¿para qué sirve el parámetro `data`?

> 🤔 Para pensar: Hmm, funcionó, pero ¿creó el contenido que queríamos? ¿Por qué?


El servidor de QMP necesita que le especifiquemos el tipo de contenido, para que cuando creemos algo sepa de qué tipo de cosa estamos hablando. Usemos para eso la cabecera que vimos anteriormente: `Content-Type`


```python
>>> import json, requests
>>> headers = {'Content-type': 'application/json', 'Accept': 'text/plain'}
>>> data =  { "tipo": "chomba", "talle": "XS" }
>>> r = requests.post('https://macowins-server.herokuapp.com/prendas', data=json.dumps(data), headers=headers)
>>> r.status_code
201
>>> requests.get('https://macowins-server.herokuapp.com/prendas').json()
```

> 🏅 Desafío: Nos quedaron prendas con ids que no nos sirven; ¡borralas!

> 📝 Nota: el servidor de QMP aceptó la prenda aún sin especificar el tipo de contenido, pero la  guardó de una forma incorrecta. Otros servidores podrían haber hecho un intento por descubrir  el tipo de
> todas maneras, o haber rechazado el pedido completamente, con un error de la familia `400`.

Como vemos, haciendo POST sobre la ruta de `/prendas` creamos una prenda, sin especificar un id, dado que se generará solo. De todas formas, si quisieramos podríamos haberlo especificado
agregándolo en el cuerpo.

> 🏅 Desafío XIII: Creá una venta.

> 🏅 Desafío XIV: Intentá hacer POST sobre una venta concreta, como por ejemplo `https://macowins-server.herokuapp.com/prendas/1`. ¿Qué sucede?

## 10. Sobre la semántica de los verbos

> 🤔 Para pensar: A los métodos HTTP también se les dice verbos. ¿Por qué?

Como vemos, hay varios verbos (métodos) HTTP:

* `OPTIONS`
* `GET`
* `POST`
* `PUT`
* `PATCH`
* `DELETE`

Nada nos impide borrar con GET, eliminar con POST o consultar con PUT. ¡Son todas convenciones!
Estas convenciones nos hablan de una semántica para cada uno de los verbos, y es importante respetarlas:

* `OPTIONS`: consultar meta-datos o configuraciones de HTTP
* `GET`: consultar un contenido sin efecto
* `POST`: crear un contenido
* `PUT`: actualizar de forma total un contenido
* `PATCH`: actualizar de forma parcial un contenido
* `DELETE`: eliminar un contenido

> 🤔 Para pensar: ¿por qué es importante respetar estas convenciones?

> 🤔 Para pensar: `POST` es uno de los métodos con efecto más antiguos de HTTP, y por eso es común que a veces se lo use
> para resolver operaciones que no encajan en otras semánticas. ¿Se te ocurre algún otro ejemplo fuera de HTTP en que pase algo así?


## 11. Recursos

Formalización de REST: 
REST es un tipo de arquitectura de desarrollo web que se basa en el uso correcto de URLs y HTPP.
Organizaremos nuestras rutas, tanto de una API como de **un sitio común y corriente**, en forma de recursos y _colecciones_.

* `GET /ventas/`: consultar todos (listar)
* `DELETE /ventas/`: borrar todos
* `POST /ventas/`: crear uno
* `POST /ventas/1` crear uno con ID (QMP no lo soporta)
* `GET /ventas/1`: consultar uno
* `PUT /ventas/1`: modificar uno
* `DELETE /ventas/1`: eliminar uno

> 🤔 Para pensar: nuevamente, ¿por qué es importante respetar estas convenciones?

Existen algunas reglas básicas para escribir las rutas REST:

- Debe evitarse usar verbos
- No debemos tener más de una URI para identificar un mismo recurso
- Deben ser independiente de formato
- Deben mantener una jerarquía lógica
- Los filtrados de información de un recurso no se hacen en la URI

> 🏅 Desafío XV: ¿cuales de los siguientes sitios tiene (o parecen tener, al menos) rutas REST?
>
>   * Github
>   * Youtube
>   * Facebook
>   * Infobae, Pagina12, La Nacion
>   * UNQ, UCEMA
>
> 🏅 Desafío XVI: si no se organizan de forma REST, ¿cómo se organizan sus rutas?

> 💬 Para discutir: recursos anidados

> 🏋️ Ejercicio: Pongamos a prueba nuestros conocimientos de REST [con este problema](https://docs.google.com/document/d/1CS15yIqbjJuiMuuMT1XPQZA6eDGSBoU9mrfhMde2IXM/edit?usp=sharing)

## 12. Paréntesis: servidores y despliegue

> 🤔 Para pensar: ¿Dónde está desplegada nuestra API? ¿En la máquina de uno de los docentes? ¿En tu máquina? ¿Qué problemas tendría ésto?

> 🏅 Desafío XVII: ¿En dónde está desplegado QMP? ¿Podés averiguarlo las cabeceras HTTP y/o la URL?

> 💬 Para discutir: qué es Heroku y cómo se despliega allí
