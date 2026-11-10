# 03-instalacion-proxmox

## Objetivo

Instalar y configurar el hipervisor Proxmox VE dentro de una máquina virtual en VirtualBox, habilitando la virtualización anidada para ejecutar sistemas invitados, y verificar el acceso al panel de gestión web.


## Procedimiento

1. Se verificó la versión de VirtualBox instalada en el equipo anfitrión.
2. Se creó una VM Linux de 64 bits asignando 4 vCPU, 8 GB de RAM y un VDI de 80 GB dinámico, reservando recursos suficientes para el host físico.
3. Con la VM apagada, se habilitó la opción "VT-x/AMD-V anidado" en la configuración del procesador para permitir KVM.
4. Se asignaron los adaptadores de red (NAT y Solo-anfitrión) siguiendo el esquema de diseño previo.
5. Se montó la ISO autorizada y se procedió a la instalación dentro del VDI.
6. Se estableció el hostname (`pve-ehifel`), el DNS y la IP de gestión (`192.168.56.10`).
7. Se abrió el panel de control web desde el navegador del equipo anfitrión comprobando el acceso.



## Comandos usados


```bash
hostnamectl
ip -br addr
pveversion
df -h
```

## Evidencias


Salida de hostnamectl:

 Static hostname: pve
       Icon name: computer-vm
         Chassis: vm 🖴
      Machine ID: fa1ad060c50646f6b4a6732932a3c298
         Boot ID: d6b699f5f01a4cb6972a59aff7dec1f9
    Product UUID: 0a226a1f-091e-5949-ba23-5fa7b821b805
  Virtualization: oracle
Operating System: Debian GNU/Linux 13 (trixie)
          Kernel: Linux 7.0.2-6-pve
    Architecture: x86-64
 Hardware Vendor: innotek GmbH
  Hardware Model: VirtualBox
 Hardware Serial: VirtualBox-1f6a220a-1e09-4959-ba23-5fa7b821b805
Firmware Version: VirtualBox
   Firmware Date: Fri 2006-12-01
    Firmware Age: 19y 11month 1w 2d


Salida de ip -br addr:

lo               UNKNOWN        127.0.0.1/8 ::1/128
nic0             UP
nic1             UP
vmbr0            UP             10.0.2.15/24 fe80::a00:27ff:fee2:6a62/64
vmbr1            UP             192.168.56.10/24 fe80::a00:27ff:fec2:4635/64

Salida de pveversion:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "es_ES.UTF-8",
        LC_NUMERIC = "es_ES.UTF-8",
        LC_COLLATE = (unset),
        LC_TIME = "es_ES.UTF-8",
        LC_MESSAGES = (unset),
        LC_MONETARY = "es_ES.UTF-8",
        LC_ADDRESS = "es_ES.UTF-8",
        LC_IDENTIFICATION = "es_ES.UTF-8",
        LC_MEASUREMENT = "es_ES.UTF-8",
        LC_PAPER = "es_ES.UTF-8",
        LC_TELEPHONE = "es_ES.UTF-8",
        LC_NAME = "es_ES.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
pve-manager/9.2.2/b9984c6d90a4bd80 (running kernel: 7.0.2-6-pve)



Salida de df -h:

Filesystem            Size  Used Avail Use% Mounted on
udev                  1.4G     0  1.4G   0% /dev
tmpfs                 392M  1.2M  391M   1% /run
/dev/mapper/pve-root   31G  4.2G   25G  15% /
tmpfs                 2.0G   46M  1.9G   3% /dev/shm
tmpfs                 5.0M     0  5.0M   0% /run/lock
tmpfs                 1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
tmpfs                 2.0G     0  2.0G   0% /tmp
/dev/fuse             128M   16K  128M   1% /etc/pve
tmpfs                 1.0M     0  1.0M   0% /run/credentials/getty@tty1.service
tmpfs                 392M  4.0K  392M   1% /run/user/0



## Incidencias

Si el sistema alerta sobre la falta de soporte KVM para los invitados, se debe a que la opción de virtualización anidada de VirtualBox no se aplicó correctamente. Como prevención, se activó obligatoriamente en los ajustes del procesador de la VM antes de arrancar la ISO, lo que garantiza la disponibilidad del módulo.



## Conclusion

El hipervisor Proxmox VE ha sido desplegado exitosamente en VirtualBox. El acceso al panel de administración (TCP 8006) funciona desde la red del anfitrión y los comandos validan que el direccionamiento, la versión del sistema y el particionado del almacenamiento base están listos para las siguientes fases del laboratorio.



[Volver al indice](../README.md)
