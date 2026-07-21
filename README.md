# Laboratorio SAMBA

## 1. Instalación y Creación de la Máquina Ubuntu Server

Lo primero de todo, vamos a necesitar descargar la imagen ISO de Ubuntu Server. Una vez que la tengamos en nuestro equipo, abrimos VirtualBox y nos preparamos para el proceso.

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/0bc191a78ed113a86c3f0d886edc3f45f57d0d73/Captura%20de%20pantalla%202026-07-15%20185054.png" alt="Configuración de red Host-Only en VirtualBox" width="80%" />
</p>

---

### 1.1 Creamos la máquina virtual

Hacemos clic en **Nueva** dentro de VirtualBox y completamos los campos correspondientes.

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/6dd2f14e799c96b01ec641f8e0ab0f681ffb002a/cap2.png" alt="Creación de la máquina virtual en VirtualBox - Paso 1" width="80%" />
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/f960d9ed13795e5ddc80984663cbb7f730d308cf/cap3.png" alt="Creación de la máquina virtual en VirtualBox - Paso 2" width="80%" />
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/f960d9ed13795e5ddc80984663cbb7f730d308cf/cap4.png" alt="Creación de la máquina virtual en VirtualBox - Paso 3" width="80%" />
</p>

Rellenamos los datos del asistente de la siguiente manera:
* **Nombre:** `Ubuntu-Server-Lab`
* **Tipo:** `Linux`
* **Versión:** `Ubuntu (64-bit)`

---

### 1.2 Asignamos los recursos de hardware

Le damos a nuestra máquina un mínimo de **2048 MB de RAM** (2 GB) y **1 CPU** para que funcione de manera fluida.

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/25b79904f989aee01887370d3a7e1abe681d158c/cap7.png" alt="Asignación de hardware en VirtualBox" width="80%" />
</p>

---

### 1.3 Configuramos el almacenamiento

Creamos un nuevo disco duro virtual de **15 GB** utilizando el formato *VDI* y seleccionamos la opción de *reservado dinámicamente* para no ocupar espacio de golpe en nuestro disco físico.

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/cc1c9ff98f5b3b7ac16a552e0465042ea8f61c52/cap5.png" alt="Configuración de disco virtual" width="80%" />
</p>

---

### 1.4 Ajustamos la configuración de red

Nos dirigimos a los ajustes de la máquina virtual que acabamos de crear. En la pestaña de **Red**, habilitamos el *Adaptador 1* y lo conectamos a la red **Adaptador solo-anfitrión (Host-Only)** que preparamos en el paso anterior.

<p align="center">
  <img src="https://raw.githubusercontent.com/gorkamonso2004/home-lab-samba/591dbb085719cd39ae4560976af59f8277dc3be5/cap6.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>

---

## 2. Configuración de Usuarios y Permisos

Para demostrar el control de acceso y la seguridad en una red corporativa simulada, crearemos dos usuarios con diferentes niveles de privilegio y un grupo de sistema:

* **Creación del grupo:** Definiremos un grupo de trabajo que tendrá permisos de escritura en la carpeta compartida.
  <p align="center">
  <img src=" https://github.com/gorkamonso2004/home-lab-samba/blob/3f820cbfc57233d488439c43827716e767f6fad4/cap8.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>
* **Usuarios a crear:**
  * `admin_lab`: Formará parte del grupo y tendrá control total (lectura y escritura).
  * `invitado_lab`: Usuario sin privilegios que solo podrá acceder en modo lectura.
 <p align="center">
  <img src="https://github.com/gorkamonso2004/home-lab-samba/blob/aebf4a6cad480cc1fb97fac1b8c00cb670bb95dd/cap9.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>

<p align="center">
  <img src="https://github.com/gorkamonso2004/home-lab-samba/blob/29272e4e26a5e9d0cff0189f2ee925540a304261/cap10.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>

* **Crear el directorio a compartir:**
<p align="center">
  <img src="https://github.com/gorkamonso2004/home-lab-samba/blob/5d603f6fae1355d636588a14f11761ecb70ac8d5/cap11.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>


---

## 3. Configuración de Samba (Servidor de Archivos)

Samba nos permite compartir carpetas y recursos de manera segura desde nuestro servidor Linux para que computadoras con Windows o macOS dentro de la misma red local puedan acceder de forma nativa.

* Instalaremos el servicio en Ubuntu Server.
  <p align="center">
  <img src="https://github.com/gorkamonso2004/home-lab-samba/blob/7eb9ef3325053f49b1c85107ff66472c35bfc8a2/cap12.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>

* Registramos los ususarios en la base de datos del Samba.
 <p align="center">
  <img src="src="https://github.com/gorkamonso2004/home-lab-samba/blob/fc34aa6033c05d002bd7c205094858c8e79244c0/cap13.png" alt="Configuración de red en VirtualBox" width="80%" />
</p>

* Configuraremos el archivo `/etc/samba/smb.conf` para estructurar la sección `[Compartido_IT]`, asignando los permisos correspondientes a nuestro grupo y definiendo las restricciones para el usuario invitado.

 <p align="center">
  <img src="src="  https://github.com/gorkamonso2004/home-lab-samba/blob/fc34aa6033c05d002bd7c205094858c8e79244c0/cap14.png"" alt="Configuración de red en VirtualBox" width="80%" />
</p>

* Guardamos el archivo y reiniciamos el servicio.

---

## 4. Conectarse desde el Sistema Principal (Host)

Una vez el servidor esté configurado y activo, realizaremos las pruebas de conectividad desde nuestro sistema operativo principal (Windows) para validar la seguridad:

1. En tu máquina física (Windows), presiona la combinación de teclas **Win + R**.
2. En la ventana de ejecutar, escribe la ruta de red:  
   `\\192.168.56.10\Compartido_IT` y presiona **Enter**.
3. **Prueba 1 (Acceso restringido):** Te pedirá credenciales. Inicia sesión como `invitado_lab` e intenta crear un nuevo archivo de texto. *(Deberías recibir un mensaje denegando el acceso).*
4. **Prueba 2 (Acceso total):** Cierra la sesión, vuelve a ingresar las credenciales usando `admin_lab` y verifica que tienes los privilegios necesarios para crear, editar y eliminar archivos o carpetas.

---
