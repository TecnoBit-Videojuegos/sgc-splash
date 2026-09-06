<div align="center">

# 🌀 SGC Splash / AutoExec DOL Launcher

### *Animación + SD2SP2 para Nintendo GameCube*

---

![Console](https://img.shields.io/badge/Console-Nintendo%20GameCube-000000?style=for-the-badge&logo=nintendo&logoColor=6A5ACD)
![Storage](https://img.shields.io/badge/Storage-SD2SP2%20%7C%20SD%20Gecko-blue?style=for-the-badge)
![FileSystem](https://img.shields.io/badge/FileSystem-FAT32-green?style=for-the-badge)

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

### 1️⃣ Descargar los archivos
Desde la sección de **Releases** de este repositorio, descarga:
* `IPL.dol` *(Lanzador principal)*
* `autoboot.rar` *(Archivos de sistema y animación)*

### 2️⃣ Configurar la tarjeta SD
Descomprime el archivo `autoboot.rar` y copia la carpeta `autoboot` resultante directamente a la raíz de tu tarjeta SD. Copia también el archivo `IPL.dol` a la raíz.

### 3️⃣ Renombrar tu aplicación por defecto
Toma el ejecutable de **Swiss** (o la app que desees), renómbralo a **`boot.dol`** y colócalo en la raíz.

---

## 📂 Estructura Final en la Tarjeta SD

Tarjeta SD (FAT32)/
├── 📄 IPL.dol                   <-- Bootloader SGC Splash
├── ⚙️ boot.dol                  <-- Aplicación principal (ej. Swiss)
└── 📁 autoboot/
    ├── 📝 autoconf.txt          <-- Configuración
    ├── 🖼️ frame_0001.png        <-- Animación (Fotograma 1)
    ├── 🖼️ frame_0002.png        <-- Animación (Fotograma 2)
    └── 🖼️ ... (hasta frame_0020.png)

---

## ⚙️ Configuración (autoconf.txt)

Abre `/autoboot/autoconf.txt` con cualquier editor de texto para ajustar los parámetros:

* **TIMER=9**: Tiempo en segundos de la cuenta regresiva antes de arrancar `boot.dol`. Usa `-1` para esperar un botón.
* **NOPRINT=1**: `1` oculta los textos en pantalla para una animación limpia. `0` muestra texto de carga.
* **DEFAULT=fat:/boot.dol**: Ruta de la aplicación que arranca al vencer el temporizador.
* **A=fat:/autoboot/autoexecA.dol**: Mapeo de botones (A, B, X, Y, L, R, ZT, S).

> ⚠️ **Nota de compatibilidad:** Las rutas y nombres de archivos son estrictamente **sensibles a mayúsculas y minúsculas** (*Case Sensitive*).

---

## 🔍 Solución de Problemas

* **Pantalla Negra:** Formatea la tarjeta SD en **FAT32** con clústeres de 32KB.
* **Sin Animación:** La carpeta debe llamarse exactamente `autoboot` en minúsculas y estar en la raíz.
* **No carga Swiss:** Confirma que el ejecutable en la raíz se llame exactamente `boot.dol`.
