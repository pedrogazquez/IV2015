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
![lsslitaz](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20111155_zps7nizp8ga.png)

Ahora instalamos el sistema con el fichero de almacenamiento virtual creado y la ISO que hemos descargado en la web de [SliTaz](http://mirror.switch.ch/ftp/mirror/slitaz/iso/stable/).

Proceso de instalación:

![proceso](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20111810_zpshjp1prey.png)

Como se puede ver instalado correctamente:
![installed](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20112236_zpsssstahae.png)

Una vez instalado este se ejecutará automáticamente sino podemos hacerlo con qemu-system-x86_64 y el fichero del almacenamiento virtual creado.

El otro sistema operativo libre que he elegido ha sido GALPon Minino, he descargado la imagen de [aquí](http://minino.galpon.org/es/descargas)

He creado  un disco duro virtual esta vez de mayor tamaño:
```
qemu-img create -f qcow2 fichero-cow2.qcow2 1G
```
Y lo he instalado con la siguiente orden usando este disco duro virtual:

```
qemu-system-x86_64 -hda fichero-cow2.qcow2 -cdrom minino-artabros-2.1_minimal.iso 
```
A continuación podemos ver el sistema operativo instalado correctamente:
![minimo](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20120446_zpsguyuqxtp.png)


## 2.2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.
He elegido VirtualBox para realizar este ejercicio, lo primero he ajustado el tamaño de ram y disco duro del nuevo sistema:
El otro hipervisor que he elegido ha sido VirtualBox y he instalado el [ttylinux](http://osarchive.sda1.eu/ttylinux).
Para realizarlo primero he configurado el virtualBox como especifico a continuación:
![configVirtual](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20121405_zpsoi8feyq7.png)

Y luego he arrancado la imagen, y aquí funcionando el ttylinux:
![ttylinux](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202016-02-02%20121542_zpspjddgyul.png)

##Ejercicios 3: Crear un benchmark de velocidad de entrada salida y comprobar la diferencia entre usar paravirtualización y arrancar la máquina virtual simplemente con qemu-system-x86_64 -hda /media/Backup/Isos/discovirtual.img.


##Ejercicios 4: Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.


##Ejercicios 5: Crear una máquina virtual ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.


##Ejercicios 6: Usar juju para hacer el ejercicio anterior.
