# Reto Contenedores I

## Crear contenedor para la BD

`
docker run -d --name my-bd-reto jmejiarojas/bd-mysql
`

## Crear contenedor para el api Personas

`
docker run -d --name api-persona -p 1603:8080 --link bd-mysql:mysql_server  jmejiarojas/api-persona-ret
`

Nota: Aplicamos `link` para comunicar ambos contenedores, "mysql_server" es el host que espera el api_persona, con el comando link es `<nombre-container>:<nombre-host-api>`

## Probamos con un curl

`curl http://localhost:1603/api/personas/rango/20/40`

### El resultado es el siguiente:

`
[{"id":1,"nombre":"william","edad":29,"sexo":"M"},{"id":2,"nombre":"pepito","edad":30,"sexo":"M"},{"id":3,"nombre":"fulana","edad":31,"sexo":"F"},{"id":4,"nombre":"mengano","edad":32,"sexo":"M"}]
`