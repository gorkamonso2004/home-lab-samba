# Laboratorio SAMBA

## 1. Instalación y Creación de la Máquina Ubuntu Server

* **Lo primero de todo, vamos a necesitar descargar la imagen ISO de Ubuntu Server.**  
<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/0bc191a78ed113a86c3f0d886edc3f45f57d0d73/Captura%20de%20pantalla%202026-07-15%20185054.png" alt="Configuración de red Host-Only en VirtualBox" width="80%" />
</p>

* **1.1 Creamos la máquina virtual:**  
  Hacemos clic en **Nueva** dentro de VirtualBox y completamos los campos con los siguientes datos:
  <p align="center">
  <img src="https://github.com/gorkamonso2004/home-lab-samba/blob/6dd2f14e799c96b01ec641f8e0ab0f681ffb002a/cap2.png" alt="Configuración de red Host-Only en VirtualBox" width="80%" />
</p>
  * **Nombre:** `Ubuntu-Server-Lab`
  * **Tipo:** `Linux`
  * **Versión:** `Ubuntu (64-bit)`

* **1.2 Asignamos los recursos de hardware:**  
  Le damos a nuestra máquina un mínimo de **2048 MB de RAM** (2 GB) y **1 CPU** para que funcione de manera fluida.

* **1.3 Configuramos el almacenamiento:**  
  Creamos un nuevo disco duro virtual de **15 GB** utilizando el formato *VDI* y seleccionamos la opción de *reservado dinámicamente* para no ocupar espacio de golpe en nuestro disco real.

* **1.4 Ajustamos la configuración de red:**  
  Nos dirigimos a los ajustes de la máquina virtual que acabamos de crear. En la pestaña de **Red**, habilitamos el *Adaptador 1* y lo conectamos a la red **Adaptador solo-anfitrión (Host-Only)** que preparamos en el paso anterior.

* **1.5 Instalamos el Sistema Operativo:**  
  Arrancamos la máquina virtual, cargamos la imagen ISO de *Ubuntu Server* que nos descargamos al principio y seguimos los pasos que nos indica el instalador. Durante este proceso, definimos nuestro usuario administrador (en nuestro caso, utilizaremos `administrador`).
