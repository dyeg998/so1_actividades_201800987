# SOLUCION ERROR 404 

### Causa:
Este problema es debido a que nginx no esta encontrando las rutas o bien paginas html creadas o renderizadas, esto debido a que en su configuracion por defecto, no tiene registradas esas rutas locales para acceder al index.html creado por el build de react.

### Solucion:
En primera instancia necesitamos crear un archivo llamado ```nginx.conf``` el cual albergara la configuracion del servidor correspondiente al que esta siendo levantado en react, dicha configuracion se describe de la siguiente manera:
```
    server {
    listen  80;

    location / {
        root   /usr/share/nginx/html;
        try_files $uri $uri/ /index.html;
        index  index.html index.htm;
    }

    }
```
En donde con el root especificamos el directorio de nginx al cual se le cargara el index.html y posteriormente hacer utilizacion de esas rutas renderizadas a partir del build de react.

Por ultimo se debe agregar una confugiracion mas al Dockerfile para que el mismo sea capaz de cargar ese archivo ```nginx.conf``` y pegarlo en la ruta local de nginx para que el mismo pueda utilizar las configuraciones del mismo.

Para eso debemos agregar los siguientes comandos:
```
RUN rm /etc/nginx/conf.d/default.conf
COPY ./nginx.conf /etc/nginx/conf.d
```

RUN rm... se utiliza para borrar cualquier configuracion por defecto que tenga el nginx y sustituirla por la conf actual que solucionara el problema y con la ultima linea de COPY se cargara lo que es el archivo ```nginx.conf``` creado en la raiz del proyecto para que el mismo pueda ser utilizado por nginx en su raiz local.