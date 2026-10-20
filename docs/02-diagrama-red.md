# 02-diagrama-red

## Objetivo

Diseñar y realizar un diagrama de red lógico y seguro para el entorno virtualizado de Proxmox. Establecer el direccionamiento IP aislado y planificar las medidas de seguridad antes de proceder con la instalación del hipervisor.

## Procedimiento

La topología se basará en dos puentes virtuales dentro de Proxmox. Los llamaremos 'vmbr0' y 'vmbr1', enlazados, a su vez, a dos adaptadores configurados en la máquina de VirtualBox:

**Adaptador 1 (NAT):** Proporcionará conectividad exterior mediante la red '10.0.2.0/24', .
**Adaptador 2 (Solo-anfitrión):** Gestionará la red aislada del laboratorio en el rango '192.168.56.0/24'.

**Nombre del nodo Proxmox:** pve-felío
**Interfaz de gestión:** 192.168.56.10 (Red Solo-anfitrión de VirtualBox).
**Bridge de Proxmox:** vmbr1, la red del laboratorio y vmbr0, la salida a Internet NAT.
**Red o VLAN de laboratorio:** 192.168.56.0/24 (Aislada físicamente).
**IPs de las VMs/LXC:** 192.168.56.20 (srv-aso) y 192.168.56.30 (cli-linux).
**Gateway y DNS:** Gateway 192.168.56.10. DNS 8.8.8.8.
**Puertos necesarios:** 8006 TCP (Panel web Proxmox), 22 TCP (SSH), y 137, 138, 139, 445 (Samba).
**Medidas de aislamiento:** Confinamiento en red Solo-anfitrión (aislado de la red del centro) y Firewall de Proxmox con política de denegación por defecto (DROP).

| Elemento | Nombre | IP | Funcion | Recursos |
|---|---|---|---|---|
| Nodo Proxmox | pve-felío | 192.168.56.10/24 | Hipervisor | 4 vCPU, 8GB RAM, 60GB |
| Servidor ASO | srv-aso | 192.168.56.20/24 | Servicio principal | 1 vCPU, 1GB RAM, 15GB |
| Cliente | cli-linux | 192.168.56.30/24 | Pruebas | 1 vCPU, 2GB RAM, 15GB |

## Comandos usados

```bash

```

## Evidencias

## Incidencias

## Conclusion

Se ha establecido un esquema de red. El laboratorio queda documentado y preparado para su posterior despliegue en la próxima sesión.

[Volver al indice](../README.md)
