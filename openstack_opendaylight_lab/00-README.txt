###########################################################
                ROOT FILESYSTEMS BUILDING
###########################################################

Para la instalación y despliegue del escenario VNX es necesario construir previamente los root filesystems de los contenedores de virtualización LXC para los nodos
de la infraestructura de integración OpenStack con OpenDayLight ("controller", "network", "computes" y "opendaylight"). Hay dos formas de hacerlo:

A) Descargar el escenario completo con los root filesystems necesarios ya generados a partir el siguiente enlace de Google Drive:
https://drive.google.com/file/d/1X3sxQEzyRAEvv45A_Aejx3Z8yp2IRy8a/view?usp=sharing

B) Construir los root filesystems manualmente haciendo uso de los scripts del directorio filesystems. Para ello, seguir los pasos indicados en "00-readme-admin.txt".
