---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

¡Bienvenido a la API de Lula! Puede usar nuestra API para acceder a nuestros endpoints. Asi podrá conseguir información sobre pisos, contactos, llamadas y mensajes en nuestra base de datos.

¡Tenemos enlaces de lenguaje en Shell, Ruby, Python y JavaScript! Puede ver ejemplos de código en el área oscura a la derecha y puede cambiar el lenguaje de programación de los ejemplos con las pestañas en la parte superior derecha.


# Autenticación

> Para ingresar use el siguiente código

```ruby
require 'lulachat'

api = lulachat::APIClient.authorize!('api_key')
```

```python
import lulachat

api = lulachat.authorize('api_key')
```

```shell
# With shell, you can just pass the correct header with each request
curl "http://lula.chat/api" \
  -H "Authorization: api_key"
```

```javascript
const lulachat = require('lulachat');

let api = lulachat.authorize('api_key');
```

> Replace `api_key` con su API key.

Lula utiliza API keys para dar acceso a nuestros datos. Para obtener una key por favor llenar el formulario de contactos en el siguiente enlace. [Lula portal](https://lula.chat/index#contact).

# Principales entidades

* Contacto: Usuario que ha llamado preguntando por información de un piso. Nos provee su información de contacto al llenar el formulario de la cita.

* Citas: Tiempo y lugar que se asigna a un agente inmobiliario y usuario.

* Pisos: Dirección donde se concretan las citas. 

* Llamadas: Evento que un usuario ejecuta al contactar a lula para reservar una cita. La llamada se da antes de la cita.



# Contactos

## Obtener mis contactos

```ruby
require 'lulachat'

api = lulachat::APIClient.authorize!('api_key')
api.lulachat.get_contacts
```

```python
import lulachat

api = lulachat.authorize('api_key')
api.lulachat.get_contacts()
```

```shell
curl "http://lula.chat/api/contacts" \
  -H "Authorization: api_key"
```

```javascript
const lulachat = require('lulachat');

let api = lulachat.authorize('api_key');
let lulachat = api.lulachat.get_contacts();
```

> El comando anterior devuelve el siguiente JSON:

```json
[
  {
    "id": 1,
    "name": "Jonathan",
    "last_name":"Diaz",
    "email": "jdiaz@gmail.com",
    "mobile": "+34506128420",
    "aval": "Nómina",
    "perfil": "Personal"
  },
  {
    "id": 2,
    "name": "Daniel",
    "last_name":"Gonzales",
    "email": "dgonzales@gmail.com",
    "mobile": "+34506483295",
    "aval": "Ahorros",
    "perfil": "Pareja"
  }
]
```

Este endpoint pide todos los contactos de la cuenta.

### HTTP Request

`GET http://lula.chat/api/contacts`



# Citas

## Obtener mis citas

```ruby
require 'lulachat'

api = lulachat::APIClient.authorize!('api_key')
api.lulachat.get_citas
```

```python
import lulachat

api = lulachat.authorize('api_key')
api.lulachat.get_citas()
```

```shell
curl "http://lula.chat/api/citas" \
  -H "Authorization: api_key"
```

```javascript
const lulachat = require('lulachat');

let api = lulachat.authorize('api_key');
let lulachat = api.lulachat.get_citas();
```

> El comando anterior devuelve el siguiente JSON:

```json
[
  {
    "cita_id": 1,
    "contact_id":1,
    "piso_id":1,
    "datetime":"2022-01-01 01:01:01"
  },
  {
    "cita_id": 2,
    "contact_id":2,
    "piso_id":1,
    "datetime":"2022-01-02 01:01:01"
  }
]
```

Este endpoint recupera todas las citas de la cuenta.

### HTTP Request

`GET http://lula.chat/api/citas`

# Pisos

## Obtener datos de mis pisos 

```ruby
require 'lulachat'

api = lulachat::APIClient.authorize!('api_key')
api.lulachat.get_pisos
```

```python
import lulachat

api = lulachat.authorize('api_key')
api.lulachat.get_pisos()
```

```shell
curl "http://lula.chat/api/pisos" \
  -H "Authorization: api_key"
```

```javascript
const lulachat = require('lulachat');

let api = lulachat.authorize('api_key');
let lulachat = api.lulachat.get_pisos();
```

> El comando anterior devuelve el siguiente JSON:

```json
[
  {
    "piso_id": 1,
    "direccion": "Calle Puigcerda 229",
    "planta" 3,
    "puerta": None,
    "llamadas": 39
  },
  {
    "piso_id": 2,
    "direccion": "Calle Radas 39",
    "planta" 2,
    "puerta": 5,
    "llamadas": 92
  }
]
```

Este endpoint recupera todos los pisos de la cuenta.

### HTTP Request

`GET http://lula.chat/api/pisos`

# Llamadas

## Obtener las llamadas

```ruby
require 'lulachat'

api = lulachat::APIClient.authorize!('api_key')
api.lulachat.get_llamadas
```

```python
import lulachat

api = lulachat.authorize('api_key')
api.lulachat.get_llamadas()
```

```shell
curl "http://lula.chat/api/llamadas" \
  -H "Authorization: api_key"
```

```javascript
const lulachat = require('lulachat');

let api = lulachat.authorize('api_key');
let lulachat = api.lulachat.get_llamadas();
```

> El comando anterior devuelve el siguiente JSON:

```json
[
  {
    "llamada_id":1,
    "piso_id": 1,
    "planta" 3,
    "puerta": None,
    "llamadas": 39
  },
  {
    "piso_id": 2,
    "direccion": "Calle Radas 39",
    "planta" 2,
    "puerta": 5,
    "llamadas": 92
  }
]
```

Este endpoint recupera todos los pisos de la cuenta.

### HTTP Request

`GET http://lula.chat/api/llamadas`