# 🎵 Audio Visualizer & Analyzer

Un analizador y visualizador de audio interactivo de alto rendimiento para la web. Utiliza **OffscreenCanvas** y **Web Workers** para delegar todo el renderizado gráfico a un hilo secundario, garantizando animaciones fluidas a 60 FPS sin bloquear la interfaz de usuario principal.

---

## 🚀 Características Principales

* **Renderizado Multihilo (Alto Rendimiento)**: Transferencia del control del canvas a un Web Worker (`worker.js`) mediante `transferControlToOffscreen()`. Esto mantiene la interfaz libre de interrupciones (*lag*).
* **Múltiples Plantillas Visuales**:
  * *Radiales*: Líneas Radiales, Radial Smooth, Espejo Radial (Línea/Smooth), Radial Blob, Radial Dots (Simple y Múltiple).
  * *Lineales*: Líneas Superiores, Ondas de Sonido, Líneas de Doble Cara, etc.
* **Detección de Pulsos (Beat Detection)**: Escala dinámica de los elementos visuales basada en el ritmo y la intensidad del audio (configurable con multiplicadores de rebote).
* **Personalización Estética**:
  * Carga de imágenes o videos de fondo (`.jpg`, `.png`, `.gif`, `.mp4`).
  * Carga de logotipos personalizados superpuestos.
  * Ajuste en tiempo real de color del trazo y del radio central del visualizador.
* **Entradas Flexibles**: Admite la carga de archivos locales (`.mp3`, `.mp4`) o la captura en tiempo real desde el micrófono.
* **Ajustes de Audio Avanzados**: Configuración en tiempo real del tamaño de la FFT (Fast Fourier Transform) y de la longitud del búfer.

---

## 🛠️ Tecnologías Utilizadas

* **Web Audio API**: Contexto de audio (`AudioContext`), decodificación de datos binarios y análisis espectral de frecuencia.
* **Web Workers & OffscreenCanvas**: Delegación del pintado en el lienzo a un hilo secundario.
* **Bootstrap 5**: Interfaz de configuración interactiva y responsiva.
* **Vanilla CSS**: Estilos avanzados para posicionamiento absoluto de canvas, video de fondo y paneles de control.

---

## 📁 Estructura del Proyecto

* **`index.html`**: Contiene la maquetación del reproductor, el lienzo (`canvas`) y el panel de configuración.
* **`style.css`**: Define los estilos visuales, efectos de cristal y posicionamiento del reproductor.
* **`script.js`**: Hilo principal que gestiona la carga de archivos, audio y la comunicación/creación del Web Worker.
* **`worker.js`**: Web Worker que recibe las frecuencias del analizador de audio y se encarga del renderizado gráfico puro en el Canvas de forma optimizada.

---

## 🔧 Configuración y Ejecución

Debido al uso de **Web Workers** y la **Web Audio API**, los navegadores bloquean la ejecución del proyecto si se abre directamente haciendo doble clic sobre el archivo `index.html` por políticas de seguridad (CORS). **Debe ser ejecutado desde un servidor local**.

### Opción 1: VS Code (Recomendado)
1. Instala la extensión **Live Server** en Visual Studio Code.
2. Abre la carpeta del proyecto.
3. Haz clic derecho sobre el archivo `index.html` y selecciona **Open with Live Server**.

### Opción 2: Python (Terminal)
Si tienes Python instalado, puedes levantar un servidor web rápido:
1. Abre tu terminal en el directorio del proyecto y ejecuta:
   ```bash
   python -m http.server 8000
   ```
2. Abre tu navegador e ingresa a `http://localhost:8000`.
