# express-logger


## Morgan

Logging es el proceso de grabar acciones y estados de la aplicación en una interficie secundaria

El _logger_ puede registrar información sobre la petición, tal como:

- El método HTTP
- URL que fue pedida
- Fecha y hora de cuando ocurrió la petición
- Cabeceras de la petición
- Origen de la petición

El registro facilita encontrar problemas en el servidor y resolverlos

[Morgan](https://github.com/expressjs/morgan) es un middleware npm, flexible y configurable, que permite manejar los registros
Instalación de Morgan:

```
$ npm install --save morgan
```
Importarlo dentro de la aplicación express:

```javascript
/* otros imports */
import morgan  from 'morgan';
```
Añadir Morgan a la pila de stacks de middlewares:

```javascript
/* other code */
app.use(
  morgan(`Request Method: :method, Request URL: :url, Response Time: :response-time(ms)`));
```
Se pueden representar partes específicas de la petición dentro de la función Morgan. Esta información se leerá y se registrará cuando se haga una petición

En este caso, registramos  `:method`, `:url`, y `:response-time`.

Hacer una petición desde una página y observar el terminal

```
Request Method: GET, Request URL: /, Response Time: 560.786(ms)
```
Morgan es fácil de configurar. Puede personalizarse la información a registrar o utilizar alguna de las opciones por defecto.


Nivel de log `dev`

```
app.use(morgan('dev'));
```

Realizar otra petición:

```
  GET / 304 99.993 ms - -
```

El nivel `dev` registra `:method`, `:url`, `:status`, `:response-time`, y `content-length`.

Los *tokens* de registro se pueden encontrar en la [documentación de Morgan](https://github.com/expressjs/morgan#tokens).

### Ejercicio

Crear un módulo de logger para registrar las peticiones que se realicen en la aplicación.
