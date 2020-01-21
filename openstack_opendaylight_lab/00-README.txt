
1 - ROOT FILESYSTEMS BUILDING

Para la instalación y despliegue del escenario VNX es necesario construir previamente los root filesystems de los contenedores de virtualización LXC para los nodos de la infraestructura de integración OpenStack con OpenDayLight ("controller", "network", "computes" y "opendaylight"). Hay dos formas de hacerlo:

A) Descargar y descomprimir el archivo del escenario completo con los root filesystems necesarios ya generados accesible a partir del siguiente enlace de Google Drive: https://drive.google.com/file/d/1nt4Gjt3LbywxAaMsKgNzodzCmcUr0grk/view?usp=sharing

B) Construir los root filesystems manualmente haciendo uso de los scripts del directorio "filesystems". Para ello, seguir los pasos indicados en "00-readme-admin.txt".


2 - Despliegue de escenario VNX openstack_opendaylight_lab

# Start the scenario
vnx -f openstack_opendaylight_lab.xml -v -t or vnx -f openstack_opendaylight_lab.xml -v --create

# Wait for all consoles to have started and configure all Openstack services (start-all)
# Load vm images in GLANCE (load-img)
vnx -f openstack_opendaylight_lab.xml -v -x start-all,load-img 

# Configure the SNMP and NRPE monitoring services necessary to test the OpenPoll monitoring tool:
vnx -f openstack_opendaylight_lab.xml -v -x start-monitoring

# Deploy a demo scenario:
vnx -f openstack_opendaylight_lab.xml -v -x create-demo-scenario
vnx -f openstack_opendaylight_lab.xml -v -x create-demo-vm3
vnx -f openstack_opendaylight_lab.xml -v -x create-demo-vm4

# Destroy the scenario
vnx -f openstack_opendaylight_lab.xml -v --destroy

# OpenStack Dashboard URL
http://10.0.10.11/horizon/auth/login/

# OpenStack Dashboard credentials
Domain: default
User Name: admin
Password: xxxx

# OpenStack nodes ("controller", "network", "compute1", "compute2" y "opendaylight") credentials
User: root
Password: xxxx

# OpenDayLight GUI DLUX URL
http://10.0.0.12:8181/index.html

# OpenDayLight credentials
User: admin
Password: admin

# Demo scenario ("create-demo-scenario", "create-demo-vm3" and "create-demo-vm4") VMs credentials
User: root
Password: xxxx


3 - Recetas para la integración de OpenStack con OpenDayLight

En el directorio "integration_recipe" se encuentra un documento PDF "Receta_OpenStack+ODL.pdf" donde se realiza una descripción detallada de cómo se ha realizado la instalación y despliegue de la plataforma OpenStack integrada con el controlador SDN OpenDayLight como proveedor de la infraestructura de red. En concreto, se trata de una receta de cómo configurar y desplegar esta infraestructura de integración a partir de un escenario configurado desde la herramienta de virtualización de redes VNX. Los pasos a seguir en este documento pueden ser utilizados para cualquier infraestructura OpenStack desplegada previamente donde se requiera la instalación e integración del controlador SDN OpenDayLight, independientemente de si se haya o no desplegado OpenStack con un escenario propio de VNX.

También hay un archivo de texto "00-notes-OpenStack+ODL.txt" donde se detallan las principales modificaciones realizadas sobre el escenario VNX de despliegue de OpenStack de partida (http://web.dit.upm.es/vnxwiki/index.php/Vnx-labo-openstack-4nodes-classic-ovs-stein) para integrar OpenDayLight como gestor de la infraestructura de red.
