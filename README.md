---

# README: becario-reels-test1

```markdown
# 📱 becario-reels-test1

Un asistente de automatización y producción de contenido de formato corto vertical (Instagram Reels, TikTok, YouTube Shorts). Diseñado para extraer momentos clave de videos horizontales o procesar fragmentos crudos para convertirlos en clips virales optimizados con reencuadre 9:16 y subtítulos dinámicos.

---

## 📋 Descripción General

`becario-reels-test1` actúa como un "editor junior virtual". Toma piezas de contenido de larga duración (podcasts, tutoriales, directos) o fragmentos directos, aplica recortes automáticos, detecta la zona de interés del rostro/acción para mantenerla centrada en 9:16, y genera subtítulos animados letra por letra con resaltados visuales.

---

## ✨ Características Principales

- **Conversión Horizontal a Vertical (16:9 a 9:16):** Reencuadre inteligente mediante seguimiento de rostro o centrado de acción.
- **Subtitulado Dinámico Estilo Reel:** Generación automática de subtítulos (usando Whisper u otros motores ASR) con estilos animados por palabra o frase.
- **Corte de Silencios y Relleno:** Eliminación automática de pausas muertas y muletillas para incrementar la retención del espectador.
- **Superposición de Elementos de Marca:** Inserción de barras de progreso, marcas de agua, llamadas a la acción y títulos superiores.
- **Exportación por Batches:** Procesamiento masivo de múltiples clips a partir de una única fuente de entrada.

---

## 🏗️ Estructura del Proyecto

```text
becario-reels-test1/
├── assets/                  # Plantillas gráficas, logos y fuentes para subtítulos
│   ├── overlays/            # Marcos 9:16, barras de progreso y gradientes
│   └── fonts/               # Fuentes en negrita optimizadas para dispositivos móviles
├── config/                  # Configuración de estilos para subtítulos y márgenes
│   └── reel_style.json      # Colores, sombras, fuentes y reglas de resaltado
├── input/                   # Contenido crudo de larga duración o archivos fuente
├── output/                  # Shorts/Reels finalizados listos para subir
├── src/                     # Módulos del procesador
│   ├── auto_cropper.py      # Algoritmo de reencuadre a 9:16 y tracking
│   ├── silence_remover.py   # Detección y corte de silencias
│   ├── subtitle_gen.py      # Transcripción ASR y renderizado de subtítulos
│   └── reel_builder.py      # Integrador final del pipeline
├── .env.example             # Plantilla para variables de entorno (claves de API)
├── generate_reels.py        # Script de ejecución
├── requirements.txt         # Lista de dependencias de Python
└── README.md
🛠️ Requisitos Previos e Instalación
Requisitos del Sistema
Python 3.8+

FFmpeg instalado y accesible en la consola.

GPU recomendada (NVIDIA con soporte CUDA) si se utiliza la transcripción local con OpenAI Whisper.

Instalación
Clonar el repositorio:

Bash
git clone [https://github.com/iasinhumo2026/becario-reels-test1.git](https://github.com/iasinhumo2026/becario-reels-test1.git)
cd becario-reels-test1
Crear y activar el entorno virtual:

Bash
python -m venv venv
source venv/bin/activate  # En Windows: .\venv\Scripts\activate
Instalar las dependencias de Python:

Bash
pip install -r requirements.txt
Configurar el archivo de variables de entorno:

Bash
cp .env.example .env
# Editar .env e introducir claves de API (OpenAI, AssemblyAI, u otros si aplica)
⚙️ Configuración del Estilo de Subtítulos
Edita config/reel_style.json para modificar el aspecto de las palabras resaltadas en pantalla:

JSON
{
  "font_name": "Montserrat-Black",
  "font_size": 48,
  "primary_color": "#FFFFFF",
  "highlight_color": "#FFE600",
  "stroke_color": "#000000",
  "stroke_width": 3,
  "position": "center_bottom",
  "margin_v": 150
}
🚀 Guía de Uso Paso a Paso
Agrega el video fuente a la carpeta input/.

Ejecuta el comando de generación indicando el archivo original y la duración deseada por clip:

Bash
python generate_reels.py --input input/podcast_ep1.mp4 --max-duration 60 --subtitles True
Revisa los resultados dentro de la carpeta output/. Cada clip generado estará listo en resolución 1080x1920.

🔍 Solución de Problemas
Uso alto de CPU/Lentitud al transcribir: Si no cuentas con GPU compatible con CUDA, configura el modelo de Whisper en modo tiny o base dentro del archivo de configuración.

Rostros cortados en el reencuadre: Si el video fuente tiene más de un sujeto, ajusta la regla de auto_cropper.py para usar modo center_crop estático o dividida (split screen).

📄 Licencia
Este proyecto está distribuido bajo la licencia MIT.
