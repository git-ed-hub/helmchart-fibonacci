# Descripcion

Para crear un helm chart
~~~sh
helm create fibonacci
~~~
Modificamos el helm con nuestros requerimientos.
Si queremos ver como quedarian los archivos configurados con las variables que colocamos, esto nos ayuda a verificar si el etiquetado es correcto:
~~~sh
# Al final es el directorio donde tienes el chart o si estas dentro del directorio colocamos "." en lugar del directorio 
helm install --dry-run debug .
# Una u otra nos muestra nuestros manifiestos.
helm install --dry-run ./fibonacci/
~~~

Creamos una plantilla de helm que despliegue la aplicacion fibonacci
El paquete de Helm cuenta con:

- Deployment
- Service
- Hpa
- Vpa
- Custom metrics
- Exponer metricas para prometheus

Para empaquetar nuestro helm ejecutamos el siguiente comando:
~~~sh
helm package fibonacci/
# Quedaria algo como lo siguiente
fibonacci-0.1.0.tgz
# movemos ese archivo dentro de nuestra carpeta charts
~~~
Para crear el repositorio de nuestro Helm
Ejecutamos el siguiente comando dentro de nuestra carpeta del helm:
~~~sh
helm repo index .
~~~


Utilizar minikube para probar (deployment, service, hpa)
Para probar (vpa, custom metrics y metricas de prometheus) instalar el script de 01_test_prometheus.md

~~~sh
minikube start
minikube addons enable metrics-server
~~~

Para instalar el helm
podemos copiar la carpeta y apuntar a su ubicacion:
~~~sh
helm install fibonacci ./fibonacci/
~~~
Dentro del apartado hay un apartado de test en el creamos un pod que revise si hay conexion con nuestro deployment

helm test fibonacci --namespace default
~~~
NAME: fibonacci
LAST DEPLOYED: Wed Nov 20 19:28:36 2024
NAMESPACE: default
STATUS: deployed
REVISION: 2
TEST SUITE:     fibonacci-test-connection
Last Started:   Wed Nov 20 19:38:45 2024
Last Completed: Wed Nov 20 19:38:51 2024
Phase:          Succeeded
~~~
