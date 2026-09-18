# ManifiestosAks-Assessment
Repositorio para desplegar manifiestos en AKS

FUNCIONES:

Trigger: Configurado en none (es un pipeline de ejecución manual para cumplir con el requisito bajo demanda).

Parámetros:

imageTag: Permite seleccionar o ingresar manualmente la versión (etiqueta) de la imagen de Docker que se desea desplegar (Con la finalidad de hacer reversos según la versión y desplegar lo que se demande).

El pipeline ejecuta las siguientes acciones mediante la CLI de Azure y kubectl:

Autenticación con AKS: Se conecta al clúster de destino utilizando la credencial de Azure configurada.

Actualización de Manifiestos: Reemplaza de forma dinámica la etiqueta de la imagen en el archivo deployment.yml con la versión especificada en el parámetro imageTag. Quien haga el despliegue ingresa manualmente la versión

Aplicación de Recursos (kubectl apply): Despliega los objetos en Kubernetes en orden lógico:

Namespace (namespace.yml)
Deployment (deployment.yml)
Service (service.yml)
Ingress (ingress.yml)
 Horizontal Pod Autoscaler (hpa.yml)

Verificación de Rollout: Espera a que el despliegue se complete correctamente (con un timeout de 180 segundos) y muestra el estado actual de los pods, despliegues y HPA.

Una vez finalice satisfactoriamente el despliegue del pipeline, se deben realizar las pruebas consumiendo el microservicio.
