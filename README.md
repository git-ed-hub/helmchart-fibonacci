# Helmchart app fibonacci

Los valores:

- hpa
- vpa
- metricsprometheus
- custom_metrics

Estan desabilitados por default

- false

En la instalacion podemos habilitarlos colocando el nombre del servicio

~~~sh
helm install <mi_chart> repositorio_del_helm --set <valores_a_habilitar>
# Elijiendo si queremos alguno en especifico o colocamos todos.
--set hpa.enabled="true"
--set vpa.enabled="true"
--set metricsprometheus.enabled="true"
--set custom_metrics.enabled="true"
~~~

o modificar el archivo values.yaml
