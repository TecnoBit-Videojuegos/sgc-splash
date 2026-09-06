SGC Splash / AutoExec DOL Launcher (Animación + SD2SP2)
¡Bienvenido! Este proyecto es un bootloader (cargador inicial) y pantalla de inicio (splash screen) altamente configurable para la consola Nintendo GameCube.

Permite:

Iniciar automáticamente una aplicación por defecto (como Swiss) al encender la consola.

Cargar aplicaciones alternativas manteniendo presionado un botón del control de GameCube.

Muestra una secuencia de imágenes animada (20 fotogramas PNG) en pantalla mientras se ejecuta la cuenta regresiva o espera la entrada del usuario.

📋 Requisitos Previos
Nintendo GameCube configurada para ejecutar archivos .dol al encender (PicoBoot, FlippyDrive, Modchip, GC Loader, IPL replacement, etc.).

Lector de tarjeta SD para GameCube:

SD2SP2 (Puerto Serial Port 2 - Prioridad principal)

SD Gecko (Adaptador de tarjeta SD en Ranura Memory Card A o B)

Tarjeta MicroSD / SD formateada obligatoriamente en FAT32.

🚀 Guía de Instalación Rápida Paso a Paso
Sigue estos sencillos pasos para dejar todo listo en tu tarjeta SD:

Paso 1: Descargar los archivos del proyecto
Ve a la sección de [Releases / Lanzamientos] de este repositorio y descarga los dos archivos:

IPL.dol (Ejecutable principal del lanzador).

autoboot.rar (Carpeta comprimida con la animación y la configuración).

Paso 2: Extraer la carpeta autoboot
Descomprime el archivo autoboot.rar en tu computadora.

Copia la carpeta autoboot resultante directamente a la raíz (raíz principal) de tu tarjeta SD.

Dentro de la carpeta autoboot/ en la SD debes tener:

El archivo de configuración autoconf.txt.

Los 20 fotogramas de la animación (frame_0001.png hasta frame_0020.png).

Paso 3: Copiar el archivo ejecutable (IPL.dol)
Copia el archivo IPL.dol directamente a la raíz de tu tarjeta SD (o renómbralo si la configuración de tu modchip/bootloader lo requiere, como en PicoBoot).

Paso 4: Colocar tu aplicación principal (boot.dol)
Descarga la última versión de Swiss (o la aplicación que desees iniciar por defecto).

Renombra el archivo .dol de Swiss a boot.dol.

Copia el archivo boot.dol en la raíz de tu tarjeta SD.

📂 Estructura Final en la Tarjeta SD
Una vez que extraigas y copies los archivos, el contenido de tu tarjeta SD debe verse exactamente así:

Plaintext
Tarjeta SD (FAT32)/
├── IPL.dol                   <-- Lanzador SGC Splash
├── boot.dol                  <-- Aplicación por defecto a lanzar (ej. Swiss)
└── autoboot/
    ├── autoconf.txt          <-- Archivo de configuración del bootloader
    ├── frame_0001.png        <-- Fotograma 1 de la animación
    ├── frame_0002.png        <-- Fotograma 2 de la animación
    ├── ...
    └── frame_0020.png        <-- Fotograma 20 de la animación
⚙️ Personalización de autoconf.txt
Puedes abrir y editar el archivo /autoboot/autoconf.txt con cualquier editor de texto (como el Bloc de Notas) en tu computadora:

Opciones Disponibles:
TIMER=9: Tiempo en segundos antes de ejecutar boot.dol automáticamente. (Usa -1 para desactivar el temporizador y esperar input).

NOPRINT=1:

1 = Oculta los textos en pantalla (ideal para una animación limpia).

0 = Muestra el texto de información de carga en pantalla.

DEFAULT=fat:/boot.dol: Ruta de la aplicación que se ejecutará al finalizar la cuenta regresiva.

Asignación de Botones en el Control:
Puedes asignar otros ejecutables .dol manteniendo presionado un botón del control al encender la consola:

A=fat:/autoboot/autoexecA.dol (Al presionar botón A)

B=fat:/autoboot/autoexecB.dol (Al presionar botón B)

X=, Y=, L=, R=, ZT= (Botón Z), S= (Botón Start)

⚠️ Importante: Las rutas y los nombres de archivos son sensibles a mayúsculas y minúsculas (Case Sensitive). Respeta las minúsculas y mayúsculas exactamente como están en la SD.

🎨 Cambiar la Animación
Si deseas reemplazar las imágenes de la animación:

Reemplaza los archivos dentro de la carpeta /autoboot/.

Las imágenes deben estar en formato PNG (mantiene la resolución recomendada de 640x480 o relación 4:3).

Nómbralas usando 4 dígitos secuenciales: frame_0001.png, frame_0002.png, etc.

🔍 Solución de Problemas Frecuentes
Pantalla negra al encender:

Verifica que la tarjeta SD esté formateada en FAT32 (exFAT o NTFS no son compatibles).

Asegúrate de que el lector SD2SP2 o SD Gecko esté bien insertado.

No muestra la animación:

Comprueba que la carpeta se llame exactamente autoboot (todo en minúsculas) y esté ubicada en la raíz de la SD.

No inicia Swiss / boot.dol:

Revisa que el ejecutable en la raíz de la SD se llame exactamente boot.dol.
