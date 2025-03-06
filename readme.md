# Agente LLM

## Guía de ejecución

### 1. Requisitos Previos

El notebook está desarrollado para ser ejecutado en Google Colab, asegúrate de tener lo siguiente:

- **Cuenta de Google:** Necesitas una cuenta de Google para acceder a Google Colab.
- **Archivo .ipynb:** Descarga el archivo Agente_LLM.ipynb desde el repositorio.
- **Archivo del Programa de Curso:** Prepara el archivo del programa de curso en formato PDF, DOCX o TXT que deseas procesar.

#### 1.2 Cómo subir el archivo .ipynb a Google Colab:

- Abre [Google Colab](https://colab.research.google.com/).
- Haz clic en Archivo > Subir notebook.
- Selecciona el archivo Agente_LLM.ipynb desde tu computadora y haz clic en Abrir.
- Una vez subido, el notebook estará listo para su ejecución.

### 2. Instalación de Dependencias en Google Colab

Las dependencias se instalan automáticamente en el notebook. Asegúrate de ejecutar todas las celdas anteriores a medida que ejecutes el notebook, para asegurarse de que el código funcione correctamente.

#### 2.1 Lista de Dependencias utilizadas:

##### 2.1.1. Bibliotecas de Python
Estas son las bibliotecas principales que se instalan mediante pip:

- **backoff:** Para manejar reintentos automáticos en caso de fallos en las solicitudes a la API.
- **python-docx:** Para leer y procesar archivos de Word (DOCX).
- **nltk:** Para procesamiento de lenguaje natural (tokenización, análisis de texto, etc.).
- **PyPDF2:** Para extraer texto de archivos PDF.
- **markdown-it-py:** Para convertir texto en formato Markdown a HTML.
- **pypandoc:** Para convertir documentos entre diferentes formatos (por ejemplo, Markdown a PDF).
- **google-generativeai:** Para interactuar con la API de Google Gemini y generar contenido educativo.

##### 2.1.2. Herramientas del Sistema
Estas herramientas se instalan en el entorno de Google Colab para permitir la conversión de documentos y la generación de PDF:

- **pandoc:** Herramienta de conversión de documentos (se usa junto con pypandoc).
- **texlive-xetex:** Paquete de LaTeX necesario para la generación de PDF con fuentes Unicode.
- **texlive-fonts-recommended:** Fuentes recomendadas para LaTeX.
- **texlive-plain-generic:** Paquetes adicionales de LaTeX para formatos genéricos.
- **fonts-freefont-ttf:** Fuentes TrueType gratuitas (como FreeSerif) que se utilizan como alternativa a Times New Roman en LaTeX.

##### 2.1.3. Recursos de NLTK
El notebook utiliza el Natural Language Toolkit (NLTK) para tareas de procesamiento de texto. Se descargan los siguientes recursos:

- **punkt:** Tokenizador de oraciones y palabras.
- **punkt_tab:** Tokenizador adicional para manejar tabulaciones y otros caracteres especiales.

##### 2.1.4. Otras Dependencias Implícitas
Además de las dependencias instaladas explícitamente, el notebook también depende de las siguientes bibliotecas estándar de Python:

- **os:** Para manejar rutas de archivos y variables de entorno.
- **json:** Para cargar y manipular archivos JSON (como las plantillas de prompts).
- **logging:** Para registrar mensajes de depuración y errores.
- **time:** Para manejar tiempos de espera y limitación de tasa.
- **re:** Para expresiones regulares (procesamiento de texto).
- **numpy:** Para cálculos numéricos (usado en la evaluación de contenido).
- **PIL (Pillow):** Para la generación de imágenes (flashcards).
- **sklearn (scikit-learn):** Para métricas de similitud de texto (evaluación de contenido).

##### 2.1.5. Dependencias de Google Colab
El notebook también utiliza funciones específicas de Google Colab, como:

- **google.colab.files:** Para cargar archivos desde el sistema local al entorno de Colab.

### 3. Ejecución del Notebook

El notebook utiliza la API de Google Gemini para generar contenido educativo. Puedes utilizar la API KEY que ya está configurada en el código o configurar tu propia clave de API. **Opciones:**

- **Usar la API KEY proporcionada:** El notebook ya incluye una API KEY que puedes utilizar para ejecutar el código sin necesidad de configurar tu propia clave.

- **Usar tu propia API KEY:**
  1. Ve a [Google Cloud Console](https://console.cloud.google.com/).
  2. Crea un nuevo proyecto o selecciona uno existente.
  3. Habilita la API de Google Gemini.
  4. Genera una clave de API desde la sección de "Credenciales".
  5. Reemplaza la API KEY en el código con tu propia clave:
     ```python
     os.environ['GOOGLE_API_KEY'] = 'TU_API_KEY_AQUI'
     ```

#### 3.1. Cargar el Archivo del Programa de Curso

El notebook está diseñado para procesar archivos de programas de curso en formato PDF, DOCX o TXT. Para cargar un archivo, sigue estos pasos:

1. Ejecuta la celda que contiene el código para cargar el archivo:
   ```python
   from google.colab import files
   uploaded = files.upload()
   ```
2. Selecciona el archivo de tu computadora y haz clic en Abrir.
3. Una vez subido, el notebook procesará automáticamente el archivo y extraerá la información necesaria.

#### 3.2. Generar Materiales Educativos

Después de cargar el archivo del programa de curso, el notebook generará automáticamente los siguientes materiales educativos:

- **Notas de Clase**: Explicaciones detalladas del tema.
- **Problemas de Práctica**: Ejercicios con soluciones paso a paso.
- **Preguntas de Discusión**: Preguntas para fomentar el debate.
- **Objetivos de Aprendizaje**: Objetivos específicos y medibles.
- **Recursos Sugeridos**: Libros, artículos y otros materiales de referencia.

#### 3.3. Guardar los Materiales Generados

Los materiales generados se pueden guardar en formato PDF o como archivos de texto. El notebook incluye funciones para:

- **Guardar en PDF**: Ejecuta la celda que convierte los materiales a PDF.
- **Guardar en Archivos de Texto**: Ejecuta la celda que guarda los materiales en archivos de texto dentro de una carpeta.

#### 3.4. Generación de Flashcards

El notebook también incluye una función para generar flashcards a partir de las preguntas de discusión y los problemas de práctica. Para generar las flashcards, ejecuta la celda correspondiente. Las flashcards se guardarán en subcarpetas dentro de cada tema, en formato PNG.

#### 3.5. Evaluación del Contenido Generado

El notebook incluye un módulo de evaluación que analiza la calidad del contenido generado. La evaluación devolverá métricas como la relevancia, consistencia, legibilidad y uso de terminología específica.

#### 3.6. Descargar los Resultados

Puedes descargar los materiales generados (PDF, archivos de texto, flashcards) utilizando el siguiente comando:

```python
from google.colab import files
files.download("materiales_curso.pdf")
```

### 4. Consideraciones Finales

- **Limitaciones de la API**: Ten en cuenta que la API de Google Gemini tiene límites en el número de tokens que puedes procesar por minuto. El notebook incluye un limitador de tasa (RateLimiter) para evitar exceder estos límites.

- **Evaluación de Contenido**: El notebook incluye una función de evaluación que mide la calidad del contenido generado en términos de relevancia, consistencia, legibilidad y uso de terminología específica.

- **Personalización:** Si deseas personalizar los prompts o ajustar la temperatura de generación para diferentes tipos de contenido, puedes modificar la configuración en la clase Config.

- **Compatibilidad:** El notebook está diseñado para ejecutarse exclusivamente en Google Colab. Para ejecutar en modo local, hay que realizar ciertas modificaciones al código, como por ejemplo usar una librería para manejar los archivos que sea compatible (pues el código utiliza la dependencia Google.colab para manejar los archivos), además de configurar correctamente un entorno virtual e instalar todas las dependencias necesarias.
