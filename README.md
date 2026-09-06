<div align="center">

# 🌀 SGC Splash / AutoExec DOL Launcher

### *Animación + SD2SP2 para Nintendo GameCube*

---

<img src="URL_DE_TU_GIF_O_IMAGEN_AQUI" alt="SGC Splash Preview" width="550" />

</div>

---

## 📖 Descripción

Un **bootloader y pantalla de inicio (splash screen)** para Nintendo GameCube que permite reproducir una secuencia de imágenes animadas al encender la consola y cargar automáticamente tu ejecutable por defecto (como **Swiss**) o aplicaciones alternativas mediante el control.

---

## ⚡ Características Principales

* 🎬 **Animación Fluida:** Carga secuencias de imágenes PNG (`frame_0001.png` a `frame_0020.png`).
* 🚀 **Auto-Boot Directo:** Ejecuta `boot.dol` automáticamente al finalizar el temporizador.
* 🎮 **Mapeo de Botones:** Inicia aplicaciones secundarias manteniendo presionado cualquier botón (A, B, X, Y, L, R, Z, Start).
* 💾 **Alta Compatibilidad:** Soporte primario para **SD2SP2** y adaptador **SD Gecko**.

---

## 📋 Requisitos Previos

1. **Nintendo GameCube** modificada (PicoBoot, FlippyDrive, Modchip, GC Loader, IPL Replacement, etc.).
2. Adaptador de tarjeta SD (**SD2SP2** recomendado en el Serial Port 2).
3. Tarjeta MicroSD / SD formateada estrictamente en **FAT32**.

---

## 🚀 Guía de Instalación Paso a Paso

### 1️⃣ Descargar los archivos necesarios
Ve a la sección de **Releases / Lanzamientos** de este repositorio y descarga los **dos archivos** disponibles:
* **`IPL.dol`**: Ejecutable principal del cargador.
* **`autoboot.rar`**: Archivo comprimido que contiene la carpeta con la animación y la configuración.

---

### 2️⃣ Extraer y copiar el contenido a la SD

1. **Copiar el ejecutable:**
   * Toma el archivo **`IPL.dol`** descargado y cópialo directamente a la **raíz de tu tarjeta SD**.
   *(Nota: Si utilizas PicoBoot u otro sistema que requiera un nombre específico, renómbralo según la exigencia de tu modchip).*

2. **Extraer la carpeta de animación:**
   * Descomprime el archivo **`autoboot.rar`** en tu computadora.
   * Copia la carpeta **`autoboot`** extraída directamente a la **raíz de la tarjeta SD**.
   *(Asegúrate de que dentro de `autoboot/` queden el archivo `autoconf.txt` y la secuencia de imágenes `frame_0001.png` a `frame_0020.png`).*

3. **Colocar tu aplicación principal:**
   * Descarga la última versión de **Swiss** (o la aplicación que quieras iniciar por defecto).
   * Renombra el ejecutable `.dol` de Swiss a **`boot.dol`** y colócalo en la **raíz de la tarjeta SD**.

---

## 📂 Estructura Final en la Tarjeta SD

<pre>
Tarjeta SD (FAT32)/
├── 📄 IPL.dol                   &lt;-- Bootloader SGC Splash
├── ⚙️ boot.dol                  &lt;-- Aplicación principal (ej. Swiss)
└── 📁 autoboot/
    ├── 📝 autoconf.txt          &lt;-- Configuración
    ├── 🖼️ frame_0001.png        &lt;-- Animación (Fotograma 1)
    ├── 🖼️ frame_0002.png        &lt;-- Animación (Fotograma 2)
    └── 🖼️ ... (hasta frame_0020.png)
</pre>

---

## ⚙️ Configuración (`autoconf.txt`)

Abre `/autoboot/autoconf.txt` con cualquier editor de texto para ajustar los parámetros:

* **`TIMER=9`**: Tiempo en segundos de la cuenta regresiva antes de arrancar `boot.dol`. Usa `-1` para esperar la entrada de un botón.
* **`NOPRINT=1`**: `1` oculta los textos en pantalla para una animación limpia. `0` muestra texto de carga.
* **`DEFAULT=fat:/boot.dol`**: Ruta de la aplicación que arranca al vencer el temporizador.
* **`A=fat:/autoboot/autoexecA.dol`**: Mapeo de botones del control (A, B, X, Y, L, R, ZT, S).

> ⚠️ **Nota de compatibilidad:** Las rutas y nombres de archivos en la tarjeta SD son estrictamente **sensibles a mayúsculas y minúsculas** (*Case Sensitive*).

---

## 🔍 Solución de Problemas

* **Pantalla Negra:** Formatea la tarjeta SD en **FAT32** (clústeres de 32KB recomendados).
* **Sin Animación:** La carpeta extraída debe llamarse exactamente `autoboot` (todo en minúsculas) y estar ubicada en la raíz.
* **No carga Swiss:** Confirma que el ejecutable de Swiss en la raíz esté renombrado exactamente a `boot.dol`.
