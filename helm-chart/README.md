# Nginx Proxy Manager Helm Chart

Este chart de Helm despliega Nginx Proxy Manager en Kubernetes utilizando los recursos de Deployment, Service y PersistentVolumeClaim.

## Requisitos previos

- Kubernetes instalado y configurado
- Helm instalado

## Instalación

### Clonar el repositorio

```shell
git clone https://github.com/Pliksys/ngynx-proxy-manager.git
```
## Instalar el chart

```shell
helm install nginx-proxy-manager <ruta-al-repositorio-helm> --namespace mi-namespace
```
Reemplaza <ruta-al-repositorio-helm> con la ruta local al repositorio del chart y <mi-namespace> con el nombre de tu namespace de Kubernetes donde deseas desplegar la aplicación.

| Parámetro                 | Descripción                                  | Valor por defecto                 |
|---------------------------|----------------------------------------------|-----------------------------------|
| `app.image`               | Imagen del contenedor de Nginx Proxy Manager | `jc21/nginx-proxy-manager:latest` |
| `app.ports`               | Puertos expuestos por Nginx Proxy Manager    | Ver valores en el values.yaml     |
| `db.image`                | Imagen del contenedor de la base de datos    | `jc21/mariadb-aria:latest`        |
| `db.MYSQL_ROOT_PASSWORD`  | Contraseña de root para la base de datos     | `npm`                             |
| `db.MYSQL_DATABASE`       | Nombre de la base de datos                   | `npm`                             |
| `db.MYSQL_USER`           | Usuario de la base de datos                  | `npm`                             |
| `db.MYSQL_PASSWORD`       | Contraseña del usuario de la base de datos   | `npm`                             |
| `service.ports.httpPort`  | Puerto HTTP público                          | `80`                              |
| `service.ports.httpsPort` | Puerto HTTPS público                         | `443`                             |
| `service.ports.adminPort` | Puerto web de administración                 | `81`                              |
| `service.type`            | Tipo de servicio                             | ``                                |
| `service.loadBalancerIP`  | IP del balanceador de carga                  | `""`                              |
| `storage.size`            | Tamaño del volumen                           | `1Gi`                             |
| `storage.nfs.server`      | Direccion servidor NFS                       | `""`                              |
| `storage.nfs.path`        | Ruta del volumen NFS                         | `""`                              |

Puedes proporcionar valores personalizados para estos parámetros utilizando el archivo values.yaml o la opción --set durante la instalación del chart.

## Acceso a la interfaz web
Una vez instalado el chart, puedes acceder a Nginx Proxy Manager a través de los puertos configurados. Para obtener más detalles sobre cómo utilizar Nginx Proxy Manager, consulta la documentación oficial.

## Desinstalar el chart

```shell
helm uninstall nginx-proxy-manager --namespace mi-namespace
```

## Actualizar el chart

```shell
helm upgrade nginx-proxy-manager <ruta-al-repositorio-helm> --namespace mi-namespace
```

## Contribuir

Si deseas contribuir a este proyecto, por favor, lee el archivo CONTRIBUTING.md para obtener más información.


## Licencia

[MIT](https://opensource.org/license/mit/) [Apache 2.0](https://opensource.org/licenses/Apache-2.0)