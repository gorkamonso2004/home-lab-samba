# Laboratorio SAMBA
## 1. Instalación y Creación de la Máquina Ubuntu Server
*  **Lo primero de todo, vamos a necesitar descargar la imagen de la ISO**
<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/0bc191a78ed113a86c3f0d886edc3f45f57d0d73/Captura%20de%20pantalla%202026-07-15%20185054.png" alt="Configuración de red Host-Only en VirtualBox" width="80%" />
</p>

*   **1.1 Crear la máquina virtual:** 
    Hace clic en **Nueva** en VirtualBox. 
    * **Nombre:** `Ubuntu-Server-Lab`
    * **Tipo:** `Linux`
    * **Versión:** `Ubuntu (64-bit)`
*   **1.2 Recursos de hardware:** 
    Asigna un mínimo de **2048 MB de RAM** (2 GB) y **1 CPU**.
*   **1.3 Almacenamiento:** 
    Crea un disco duro virtual de **15 GB** (formato *VDI*, reservado dinámicamente).
*   **1.4 Configuración de Red:** 
    Ve a la configuración de la máquina virtual, accede a la pestaña **Red**, habilita el *Adaptador 1* y conéctalo a la red **Adaptador solo-anfitrión (Host-Only)** que creaste en el paso anterior.
*   **1.5 Instalación del Sistema Operativo:** 
    Inicia la máquina, selecciona la imagen ISO de *Ubuntu Server* que descargaste y sigue los pasos del instalador. Durante el proceso, define tu usuario administrador (por ejemplo, `administrador`).


