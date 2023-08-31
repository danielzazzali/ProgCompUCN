# Guía para Principiantes en Ubuntu y Compilación de Código C++ y Python

## Contenido
1. Introduciendo Ubuntu
2. Manos a la Obra con la Terminal
3. Compilando y ejecutando Código C++
4. Compilando y ejecutando Código Python

## 1. Introduciendo Ubuntu

Ubuntu es uno de los sistemas operativos basados en Linux más populares. Con una interfaz de usuario pulida y fácil de usar, es una excelente opción para principiantes.

### Aspectos Básicos de la Interfaz de Ubuntu
- **Escritorio:** Este es el espacio de trabajo principal.
- **Barra de Tareas:** Está ubicada en la parte superior y muestra apps abiertas, el calendario, ajustes del sistema, y el menú de apagado/reinicio.
- **Dock:** Ubicado a la izquierda, contiene accesos directos a las aplicaciones.

## 2. Manos a la Obra con la Terminal

La terminal es una herramienta poderosa que permite al usuario interactuar con el sistema operativo mediante comandos de texto.

**Comandos Básicos de la Terminal**
- `cd`: Cambia el directorio actual.
- `ls`: Lista todos los archivos y directorios en el directorio actual.
- `pwd`: Muestra el directorio actual.
- `mkdir`: Crea un nuevo directorio.
- `touch`: Crea un nuevo archivo.

## 3. Compilando y ejecutando Código C++

Antes de compilar código C++, necesitamos verificar que el compilador está instalado. Si no, lo instalamos usando el comando `sudo apt-get install g++`.

**Ejemplo de Archivo C++ (hello_world.cpp)**
```cpp
#include <iostream>

int main() {
    std::cout << "¡Hola, mundo de C++!" << std::endl;
    return 0;
}
```

**Compilando y ejecutando el Archivo C++**
1. `g++ hello_world.cpp -o hello_world` (compila el código)
2. `./hello_world` (ejecuta el programa)

Verás `¡Hola, mundo de C++!` en la terminal.

## 4. Compilando y ejecutando Código Python

Python usualmente viene preinstalado en Ubuntu. Puedes confirmar esto con el comando `python3 --version`.

**Ejemplo de Archivo Python (hello_world.py)**
```python
print("¡Hola, mundo de Python!")
```

**Ejecutando el Archivo Python**
1. `python3 hello_world.py`

Verás `¡Hola, mundo de Python!` en la terminal.

---

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
