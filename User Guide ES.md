# ¿Qué es un Codebook?
Un **codebook** (o libro de códigos) es un documento de referencia que lista todos los OCFs (Original Camera Files) de una producción junto con metadatos como el nombre del clip, escena, toma, duración y referencias visuales (thumbnails). Es comúnmente utilizado en flujos de trabajo profesionales de postproducción para:

- Documentar líneas de tiempo de edición para **conform**, **pulls de VFX** o **entregas de audio**
- Revisar la organización del material durante la **edición offline y online**
- Facilitar la comunicación entre **editores, asistentes, supervisores** y **vendors externos**
- Archivar la estructura y el contenido de un proyecto para **futura restauración o re-edición**

Este script automatiza la generación de un codebook directamente desde una **línea de tiempo en DaVinci Resolve**, reduciendo el trabajo manual y mejorando la precisión.
![[Screenshot 2025-05-19 at 10.03.45.png]] 
___
# Descripción General: DB_Codebook_Generator_v2.2.4.py

**DB_Codebook_Generator_v2.2.4** es un script personalizado para DaVinci Resolve que:

- Extrae datos de los clips en la línea de tiempo
- Captura un cuadro (thumbnail) de cada clip
- Exporta una hoja de cálculo `.xlsx` completamente formateada con thumbnails y metadatos incrustados
- Organiza los resultados en una carpeta limpia y contenida para fácil distribución o archivo
___
# Contenido de esta guía
1. Requisitos 🔧
2. Instalación 📂
3. Cómo usar el script 🧩
4. Estructura de salida y metadatos 📊
5. Solución de problemas 🛠️
6. Soporte y contacto 💬
___
## 🔧 Requisitos

ara usar **DB_Codebook_Generator_v2.2.4**, necesitas lo siguiente:

- **DaVinci Resolve Studio** (última versión recomendada)
- **Python 3.7 o superior**
- Bibliotecas de Python instaladas:
    - `openpyxl`
    - `pillow` (o `PIL`)

Puedes instalar las bibliotecas necesarias con pip:

```bash
pip install openpyxl pillow
```

___
## 📂 Instalación

1. **Descarga el archivo del script**  
    Asegúrate de tener el archivo:  
    `DB_Codebook_Generator_v2.2.4.py`
2. **Ubica el directorio de scripts de Resolve**
    - **macOS**:  
        `~/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Scripts/Edit`
    - **Windows**:  
        `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Fusion\Scripts\Edit`
3. **Copia el script**  
    Pega el archivo `.py` en la carpeta de scripts `Edit`.
4. **Reinicia DaVinci Resolve**  
    Esto permite que Resolve cargue el nuevo script.

Una vez instalado, el script aparecerá en Resolve en:

**Workspace > Scripts > Edit > DB_Codebook_Generator_v2.2.4**
___
## 🧩 Cómo usar el script

Una vez instalado el script y con DaVinci Resolve abierto, sigue estos pasos:

### 1.Abre tu Proyecto y Timeline

Inicia **DaVinci Resolve Studio** y abre el proyecto y la línea de tiempo desde la que deseas generar el codebook.

### 2. Ejecuta el script

Ve a:

`Workspace > Scripts > Edit > DB_Codebook_Generator_v2.2.4`


>[!CAUTION] 
>El script solo funciona en la línea de tiempo activa, así que asegúrate de que la línea de tiempo deseada esté abierta y visible en la página de edición.
>
>En la versión 2.2.4, el script solo admite una pista de video a la vez. Si tu línea de tiempo tiene varias pistas, puedes desactivar todas excepto una y correr el script varias veces. Los clips desactivados se ignorarán.

### 3. Configura las opciones de exportación

Aparecerá una ventana del script. Podrás personalizar:
![[Screenshot 2025-05-19 at 9.59.42.png]]
Aparecerá una ventana del script. Podrás personalizar:

- **Campos de metadatos**: Elige qué campos incluir en la hoja de cálculo (p. ej., Nombre del clip, Escena, Toma, Reel, Especificaciones de audio, etc.)
- **Posición del cuadro para el thumbnail**:
    - Primer cuadro
    - Cuadro medio (recomendado)
    - Último cuadro
- **Tamaño del thumbnail**: Elige entre pequeño, mediano o grande
- **Carpeta de salida**: Selecciona dónde se guardará el archivo `.xlsx` y los thumbnails
- **Eliminar Stills después de exportar**: Activa esta opción para limpiar la galería de Resolve tras exportar

>[!CAUTION] 
>La opción **"Eliminar Stills después de exportar"** eliminará **todos los stills** de la galería actual, no solo los generados por el script.
>
>Para evitar pérdida de información, se recomienda **respaldar tus stills** existentes y crear una **galería dedicada** para este script.

> [!NOTE] 
>Los thumbnails se generan a partir de capturas dentro de la línea de tiempo y se incrustan directamente en el archivo Excel.
>
>El script guarda automáticamente tu configuración más reciente en:  
**macOS y Windows:** `~/Documents/ResolveCodebook/codebook_settings.json`
>
>Esto permite que el script precargue tus preferencias la próxima vez que lo uses ahorrando tiempo en futuras exportaciones.

### 4. Elige ubicación y nombre del archivo de exportación

Después de hacer clic en **"Generate Codebook"**, el script te guiará para seleccionar dónde y cómo guardar la exportación:

1. Una ventana de **Finder (macOS)** o **Explorer (Windows)** te pedirá seleccionar el **directorio de exportación**
2. Luego, aparecerá un cuadro de diálogo para **nombrar tu archivo de codebook**
    - El nombre predeterminado será:  
        `ProjectName_TimelineName_Codebook.xlsx`
![[Screenshot 2025-05-19 at 10.00.25.png]]

> [!IMPORTANT]  
> El script no guarda los archivos directamente en la carpeta seleccionada.  
Crea una **subcarpeta con el nombre del archivo codebook** (sin la extensión `.xlsx`) 
>
>El archivo Excel y los thumbnails se guardan dentro de esta subcarpeta.

### 5. Genera el codebook

Una vez confirmados el destino y nombre del archivo, el script:

- Procesará todos los clips válidos en la línea de tiempo
- Extraerá los campos de metadatos seleccionados
- Capturará una imagen fija del cuadro especificado (primero, medio o último)
- Generará un archivo `.xlsx` con thumbnails incrustados y metadatos estructurados

✅ Aparecerá un mensaje de confirmación cuando la exportación se complete con éxito.
![[Screenshot 2025-05-19 at 10.00.45.png]]
___
## 📊 Estructura de salida y metadatos

Después de exportar, el script genera una **subcarpeta** dentro de la ubicación que seleccionaste. Tanto el archivo `.xlsx` como las imágenes se guardan juntos.

### 🗂 Estructura de carpeta

`/[TuUbicaciónExportada]/DB_ProjectName_TimelineName_Editorial_Codebook/`  
`├── DB_ProjectName_TimelineName_Editorial_Codebook.xlsx`  
`├── thumb_0.jpg`  
`├── thumb_1.jpg`  
`├── thumb_2.jpg`  
`└── ...`

- La subcarpeta toma el nombre de tu **proyecto y línea de tiempo en Resolve**
- Todos los elementos — incluyendo el `.xlsx` y **thumbnails numerados secuencialmente** (`thumb_0.jpg`, etc.) — están en el **mismo directorio** por conveniencia
![[Screenshot 2025-05-19 at 10.01.02.png]]

> [!NOTE] 
> Puedes cambiar el nombre o mover esta carpeta después de exportar si lo necesitas.

---

### 🧾 Campos de metadatos

La hoja de cálculo incluye metadatos de cada clip según tu selección. Campos comunes incluyen:

- Nombre del clip
- Escena / Toma
- Reel
- Tarjeta
- Timecode de inicio / fin
- Resolución
- Codec
- Canales de audio
- Color tag
- Comentarios

> [!TIP] 
> Los campos están ordenados colocando primero los esenciales para edición (como Nombre del clip, Escena y Toma), seguidos del resto en orden alfabético.

---

### 🖼 Thumbnails

Cada entrada en el archivo `.xlsx` incluye un thumbnail del clip en la línea de tiempo:

- Puedes elegir entre el **Primer**, **Medio** o **Último** cuadro
- Los thumbnails están **incrustados directamente** en el archivo Excel
- El **tamaño** se puede ajustar desde la interfaz del script
![[Screenshot 2025-05-19 at 10.01.26.png]]
___
## 🛠️ Troubleshooting

Si algo no funciona como esperas, aquí algunas causas comunes y cómo resolverlas:

### ❌ El script no aparece en Resolve

- Asegúrate de que el archivo `DB_Codebook_Generator_v2.2.4.py` esté en la carpeta correcta:
    - **macOS**:  
        `~/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Scripts/Edit`
    - **Windows**:  
        `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Fusion\Scripts\Edit`
- Verifica que estés en la página `Edit` de Resolve
- Reinicia Resolve después de copiar el script

### ❌ El script no se inicia o se cierra de inmediato

- El script depende del **DaVinci Resolve Script Module** (`DaVinciResolveScript.py`)
- Si este módulo **no se encuentra**, el script no se ejecutará

#### ✅ Cómo solucionarlo:

1. Ubica el archivo `DaVinciResolveScript.py` oficial
    - Suele encontrarse en el directorio de instalación de Resolve o en el SDK
2. Copia `DaVinciResolveScript.py` en la **misma carpeta** que `DB_Codebook_Generator_v2.2.4.py`
3. Reinicia Resolve e inténtalo de nuevo

> [!TIP]
>  Puedes abrir la **consola de DaVinci Resolve** (Workspace > Console) para revisar errores o mensajes faltantes.
### ❌ El archivo Excel está vacío o faltan datos

- Asegúrate de que haya una **línea de tiempo abierta y activa**
- El script solo funciona con **clips visibles y habilitados** en una **sola pista de video**
- Desactiva las demás pistas de video e inténtalo de nuevo

### ❌ Faltan thumbnails

- Verifica que:
    - Los clips no estén offline
    - No estés usando títulos, generadores o composiciones de Fusion
    - Resolve esté generando correctamente los stills

### ⚠️ “Eliminar Stills después de exportar” borró más de lo esperado

- Esta opción borra **todos los stills** de la galería activa — no solo los generados por el script
- Para evitar pérdida de datos:
    - **Respalda tus stills importantes**
    - Usa una **galería de stills dedicada** durante la exportación

### 🐍 Errores de Python o el script se cierra

- Asegúrate de tener instalado Python 3.7 o más reciente
- Instala las bibliotecas necesarias:

  ```bash
  pip install openpyxl pillow
  ```
- Revisa la **Consola** de Resolve y la carpeta de logs:
	- `Help > Reveal Log Folder`

>[!NOTE] 
> Si sigues teniendo problemas, comparte la salida de consola o logs y contacta soporte.

___
## 💬 Soporte y retroalimentación

¿Tienes preguntas, encontraste un bug o quieres sugerir una mejora?

Mantengo activamente este script y agradezco cualquier feedback de editores, asistentes, supervisores de post y cualquier persona que lo use en flujos reales.

### 📨 Contacto

- **Email:** dany.b@dandbc.mx
- **GitHub:** [github.com/dandbc](https://github.com/dandbc)
- **Buy Me a Coffee:** [buymeacoffee.com/dandbc](https://www.buymeacoffee.com/dandbc)

> ☕ Si esta herramienta te ahorró tiempo o ayudó en tu proyecto, considera apoyar el desarrollo futuro con un cafecito.

---
### 🙌 Contribuye

Si quieres aportar al proyecto:

- Haz un fork del repositorio en GitHub
- Envía pull requests o abre issues
- Comparte la herramienta con colegas de postproducción

Hagamos que las partes aburridas de la post sean un poco menos aburridas — juntos.
