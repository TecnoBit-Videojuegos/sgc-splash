# SGC Splash / AutoExec DOL Launcher con Animación (SD2SP2 Support)

Este proyecto es un bootloader y splash screen configurable para Nintendo GameCube. Permite iniciar automáticamente una aplicación ejecutable (como **Swiss**) desde un dispositivo SD o seleccionar diferentes aplicaciones presionando botones al encender la consola.

Está diseñado para funcionar como un reemplazo directo del ejecutable inicial (**`IPL.dol`**) y cuenta con soporte para mostrar una **secuencia de imágenes animada** en pantalla mientras espera la acción del usuario o el tiempo de arranque automático.

---

## 🛠️ Características Principales

* **Compatibilidad Multidispositivo:** Detecta y monta automáticamente la tarjeta SD desde:
  * **SD2SP2** (Serial Port 2 - Prioridad primaria)
  * **Slot A** (SD Gecko en ranura de Memory Card A)
  * **Slot B** (SD Gecko en ranura de Memory Card B)
* **Boot Animado:** Muestra una secuencia de fotogramas (imágenes PNG) en forma de ciclo o flipbook mientras corre el temporizador.
* **Mapeo de Botones:** Carga archivos `.dol` específicos dependiendo del botón presionado al arrancar.
* **Fallback de Seguridad:** Si no encuentra la ruta configurada, intentará cargar automáticamente `fat:/boot.dol` o `fat:/autoexec.dol`.

---

## 📁 Estructura del Archivo `.zip` de Lanzamiento

Al descargar la release comprimida (**`sgc-splash-animado.zip`**), dentro encontrarás:

```text
sgc-splash-animado.zip
└── IPL.dol   <-- Ejecutable listo para usar en tu GameCube (reemplazo de IPL/Bootloader)
