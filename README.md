# Helmchart app fibonacci

~~~sh
helmchart-fibonacci/
├── charts
│   └── fibonacci-0.1.0.tgz
├── Chart.yaml
├── index.yaml
├── README.md
├── templates
│   ├── custommetrics.yaml
│   ├── deployment.yaml
│   ├── _helpers.tpl
│   ├── hpa.yaml
│   ├── NOTES.txt
│   ├── servicemonitor.yaml
│   ├── service.yaml
│   ├── tests
│   │   └── test-connection.yaml
│   └── vpa.yaml
└── values.yaml
~~~

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
