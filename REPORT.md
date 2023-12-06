# Lab 6 - Microservicios

## Task 1. Create your own configuration repository and update the configuration of your service `config` to use it
En primer lugar, se ha clonado el repositorio que contiene la configuración y se ha modificado en el servicio `config` 
el archivo `application.yml` para incluir este repositorio.
El link del repositorio clonado es el siguiente:

- https://github.com/Patriigb/lab6-microservices-config-repo

## Task 2. Two services `accounts (2222)` and `web` are running and registered
A continuación, se han ejecutado los servicios `accounts` y `web`, como se puede ver en las siguientes imágenes:

![ServiceAccounts.png](Images%2FServiceAccounts.png)

![ServiceWeb.png](Images%2FServiceWeb.png)

## Task 3. The service `discovery` has these two services registered
Después, con el servicio `discovery`, se puede acceder a [Eureka](https://github.com/Netflix/eureka) y ver que se encuentran los dos servicios 
anteriores registrados:

![Eureka.png](Images%2FEureka.png)

## Task 4. Update the configuration repository so that the `accounts` service uses now the port 3333
Una vez hecho esto, se va a cambiar el puerto que usa el servicio `accounts (2222)` por otro diferente `(3333)`. Esta 
modificación corresponde al siguiente commit:

https://github.com/Patriigb/lab6-microservices-config-repo/commit/f28ef295391917140ea26674ae4005a1266b9d38

## Task 5. Run a second instance of the `accounts` service using the new configuration
Si ahora se vuelve a lanzar un segundo servicio `accounts`, se ejecutará en el puerto `3333`, que es el que aparece en la 
configuración. A continuación se muestra lo que ocurre en Eureka:

![Eureka2.png](Images%2FEureka2.png)

Se observa que el servicio `accounts` aparece duplicado, ya que se encuentra registrado tanto en el puerto `2222` como en 
el `3333`.

## Task 6. What happens when you kill the service `accounts (2222)` and do requests to `web`?
Si se quita el servicio `accounts (2222)`, sale en la página web un mensaje avisando sobre que puede haber instancias no 
disponibles. Esto ocurre porque ha detectado que el servicio del puerto `2222` ya no está activo.

![Eureka3.png](Images%2FEureka3.png)

Sin embargo, al volver a actualizar la página, solo aparece registrado el servicio que estaba en el puerto `3333`.

![Eureka4.png](Images%2FEureka4.png)

## Task 7. Can the web service provide information about the accounts again?
Finalmente, en la siguiente imagen se puede comprobar que la información de `accounts` está disponible, aunque esta vez en
el puerto `3333` y sin tener que haber lanzado todo de nuevo al cambiar el puerto.

![Account.png](Images%2FAccount.png)

