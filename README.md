- Generar una imagen dentro de Openshift desde un archivo local

Estructura del proyecto:
path/to/project/
    Dockerfile

Pasos:
1-Nos logueamos al cluster
> oc login ...

2-Creamos el proyecto
> oc new-project binary-build

3-Creamos un nuevo BuildConfig con la estrategia docker
> oc new-build --name test-binary-build --binary --strategy docker

4-Nos ubicamos en el directorio de nuestro proyecto donde se encuentra el Dockerfile
> cd /path/to/project

5-Iniciamos el build
> oc start-build test-binary-build --from-dir .

Con estos pasos, ya vamos a tener una imagen personalizada lista para utilizar dentro de Openshift.

OPCIONAL:

6-Creamos nuestra aplicación en base a la imagen pusheada 
> oc new-app test-binary-build 

7-Exponemos el servicio mediante la creación de una ruta
> oc expose svc/test-binary-build
