##Ejercicios 1: Instalar los paquetes necesarios para usar KVM. Se pueden seguir estas instrucciones. Ya lo hicimos en el primer tema, pero volver a comprobar si nuestro sistema está preparado para ejecutarlo o hay que conformarse con la paravirtualización.
He instalado KVm con el siguiente comando:
```
aptitude install qemu-kvm libvirt-bin
```
Una vez hecho esto he ejecutado sudo kvm-ok y me ha devuelto el siguiente mensaje:
```
 INFO: Your CPU does not support KVM extensions KVM acceleration can NOT be used
```

Por lo que mi sistema no soporta virtualización de KVM.

##Ejercicios 2: 1. Crear varias máquinas virtuales con algún sistema operativo libre tal como Linux o BSD. Si se quieren distribuciones que ocupen poco espacio con el objetivo principalmente de hacer pruebas se puede usar CoreOS (que sirve como soporte para Docker) GALPon Minino, hecha en Galicia para el mundo, Damn Small Linux, SliTaz (que cabe en 35 megas) y ttylinux (basado en línea de órdenes solo). 
La primera máquina virtual que he creado a sido una con SliTaz, primero he creado un disco duro virtual en formato QCOW2 con:
```
qemu-img create -f qcow2 fichero-cow.qcow2 200M
```
![lsslitaz](qemu-img create -f qcow2 fichero-cow.qcow2 200M)
## 2.2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.


##Ejercicios 3: Crear un benchmark de velocidad de entrada salida y comprobar la diferencia entre usar paravirtualización y arrancar la máquina virtual simplemente con qemu-system-x86_64 -hda /media/Backup/Isos/discovirtual.img.


##Ejercicios 4: Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.


##Ejercicios 5: Crear una máquina virtual ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.


##Ejercicios 6: Usar juju para hacer el ejercicio anterior.
