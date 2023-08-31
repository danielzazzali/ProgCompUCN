## Cómo Configurar Ubuntu en una Máquina Virtual con VirtualBox
 
A continuación, se detallan los pasos para instalar Ubuntu en una máquina virtual con la función de instalación desatendida desactivada, usando VirtualBox:
 
1. **Instalar VirtualBox**: Primero, necesitarás descargar e instalar VirtualBox en tu computadora. Puedes hacerlo desde aquí: [Descargar VirtualBox](https://www.virtualbox.org/wiki/Downloads).
 
2. **Descargar la ISO de Ubuntu**: Luego, necesitarás descargar la ISO de Ubuntu. Esta ISO es la imagen del sistema operativo que instalarás en la máquina virtual. Puedes descargar la última versión desde aquí: [Descargar Ubuntu](https://ubuntu.com/download/desktop).
 
3. **Crear una nueva máquina virtual**: Una vez hayas instalado VirtualBoxy descargado la ISO de Ubuntu, abre VirtualBox y haz clic en `Nueva` para crear una nueva máquina virtual.
 
4. **Configurar la máquina virtual**: Se te pedirá que nombres tu máquina virtual. Puedes nombrarla como desees, por ejemplo "Ubuntu". En `Tipo` selecciona "Linux", y en `Versión` selecciona "Ubuntu (64-bit)" si tu equipo es de 64 bits.

5. **Asignar memoria**: El siguiente paso es asignar memoria a la máquina virtual. Para Ubuntu, se recomienda un mínimo de 2GB, pero si tienes suficiente RAM en tu computadora, puedes asignar más.

6. **Omitir la instalación desatendida**: Cuando llegues a la pantalla `Instalación Desatendida` asegúrate de desmarcar la casilla `Habilitar Instalación Desatendida`. Queremos hacer la instalación manualmente para tener más control sobre los ajustes.
 
7. **Configurar el disco duro virtual**: Selecciona la opción "Crear un disco duro virtual ahora" y haz clic en `Crear`. Elige "VDI (Imagen de Disco Duro de VirtualBox)". A continuación selecciona "Reservado dinámicamente".
 
8. **Asignar espacio de disco duro**: Deberás decidir cuánto espacio de disco duro deseas asignar a tu máquina virtual. Ubuntu recomienda un mínimo de 25GB. Una vez hayas decidido, haz clic en `Crear`.
 
9. **Cargar la imagen de Ubuntu**: Ahora que has creado tu máquina virtual, selecciona la máquina que acabas de crear en la barra lateral izquierda de VirtualBox y haz clic en `Configuración`. Luego, ve a la pestaña `Almacenamiento`, selecciona `Controlador IDE` y haz clic en el ícono del CD a la derecha. Selecciona ahora "Elegir un disco" y busca la ISO de Ubuntu que descargaste y haz clic en `Abrir`. Haz clic en `Aceptar`.
 
10. **Correr la máquina virtual**: Por último, tu máquina virtual está lista para ser encendida. Haz clic en `Iniciar` y Ubuntu comenzará su instalación. Asegúrate de seguir las instrucciones en la pantalla para configurar el sistema operativo de la forma que desees. Cuando la instalación termine, tendrás una máquina virtual de Ubuntu lista para usar.
