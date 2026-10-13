# Memoria técnica: nodo Proxmox individual

La memoria presenta el resultado técnico por temas. Debe explicar cómo está construido el laboratorio, por qué se tomaron las decisiones y con qué pruebas se demostró su funcionamiento. Usa la bitácora como fuente, pero no copies el diario completo: resume la configuración final, los resultados y las limitaciones que sigan abiertas.

## Resumen

Este proyecto consiste en el diseño, instalación y configuración de un nodo de virtualización utilizando Proxmox VE. El objetivo es desplegar una infraestructura base capaz de alojar máquinas virtuales y contenedores para centralizar servicios de red corporativos, aplicando automatización y estrategias de respaldo.

## Necesidad y objetivos

Necesidad que atiende el laboratorio: Se requiere consolidar múltiples servicios en un único servidor físico para optimizar los recursos de hardware, facilitar la gestión centralizada de copias de seguridad y crear un entorno aislado y seguro para el despliegue de servicios ASO.

- Objetivo comprobable 1: Instalar y configurar correctamente el hipervisor Proxmox VE, garantizando el acceso a su panel de administración web.
- Objetivo comprobable 2: Crear y desplegar plantillas base de sistemas Linux y configurar un servicio de red funcional (como Samba) accesible desde un cliente.
- Objetivo comprobable 3: Automatizar tareas de mantenimiento, como la generación de inventarios y copias de seguridad, mediante scripts en Bash y Ansible.

## Alcance y criterios de aceptación

El proyecto abarca la instalación de Proxmox en un único nodo (físico o virtualizado), la configuración de la red interna, el despliegue de máquinas virtuales/contenedores, la implementación de un servicio ASO y su automatización. 

Quedan fuera del alcance las configuraciones de Alta Disponibilidad (HA) que requieren múltiples nodos físicos, así como la integración con cabinas de almacenamiento en red complejo (SAN). El proyecto se considerará aceptado cuando el profesor pueda verificar el acceso a los servicios documentados y la correcta ejecución de los scripts de respaldo.