# Inicio

*Leer en otros lenguajes: [English](README.md), [Spanish](README.es.md)

Esto es una aplicación servidor basada en Node / Express / MongoDB que sirve para exponer los servicios públicos del Catastro disponibles en http://www.catastro.meh.es/esp/sede.asp a la PWA del Catastro. 

La API esta desplegaada aquí [Catastro API](https://agile-reaches-32584.herokuapp.com/api)

Se han incluido otras tecnologías para extender la funcionalidad del servicio:
- [JSON Web Tokens](https://jwt.io/) - JSON Web Tokens (conocido como JWT) para securizar las llamadas no públicas de la API tales como la administración de usuarios y las operaciones CRUD sobre las localizaciones archivadas por el usuario.  
- [Mongo DB](https://docs.mongodb.com/) - MongoDB es una base de datos no relacional de código abierto que ofrece alto rendimiento, alta disponibilidad, escalado automatico y un soporte avanzado para datos georeferenciados. La estructura de datos de MongoDB está formada por pares (campo, valor) similares a JSON y GeoJSON que usados por el servidor para representar el modelo de datos.

Para correr el servidor Node localmente:

- Clonar este repo https://github.com/aurelido/catastro-node-express.git
- `npm install` para instalar todas las dependencias
- Instalar MongoDB Community Edition ([instructions](https://docs.mongodb.com/manual/installation/#tutorials)) 
- Crear directorio /data/db para los datos usados por MongoDB  `mkdir -p ./data/db`
- Arrancar MongoDB ejecutando `mongod --dbpath ./data/db/`. Ahora MogoDB debería estar corriendo en el puerto 27017
- `npm run dev` para iniciar el servidor local por defecto en el puerto 3000

# Descripción 

## Referencias
Projecto basado en https://github.com/gothinkster/react-redux-realworld-example-app

## Dependencias

- [expressjs](https://github.com/expressjs/express) - Servidor para manejar y rutear las peticiones HTTP.
- [express-jwt](https://github.com/auth0/express-jwt) - Plataforma para la validacion de JWTs utilizados para la seguridad de ciertos recursos de la API.
- [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) - Generación de JWTs usado para autentificación del usuario.
- [mongoose](https://github.com/Automattic/mongoose) - Modelo y mapeo de datos MongoDB en Javascript.
- [mongoose-unique-validator](https://github.com/blakehaswell/mongoose-unique-validator) - Validacion de valores unicos y generación de errores en Mongoose. Mongoose solo ofrece validación a nivel de documento (representación de un objeto en MongoDB), por lo que un índice único a lo largo de una colección lanzará una excepcion a nivel del connector. El plugin `mongoose-unique-validator` nos ayuda formateando estos errores como una validacion `ValidationError` de Mongoose.
- [passport](https://github.com/jaredhanson/passport) - Autentificaión de usuarios.

## Estructura de la aplicación

- `app.js` - Punto de entrada de nuestra aplicación. Este archivo define nuestro servidor express y connecta con la instancia MongoDB usando mongoose.
- `config/` - Directorio que contiene la configuracion para passport asi como el contenedor como punto central para la configuración de variables de entornos en configuration/environment.
- `routes/` - Directorio que contiene la definion de las rutas de nuestra API.
- `models/` - Directorio que contiene el modelo de datos usado por Mongoose.