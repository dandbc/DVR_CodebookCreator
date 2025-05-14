# 🎬 DB Codebook Generator for DaVinci Resolve Studio

A DaVinci Resolve Studio script that generates a fully formatted Excel codebook from the current timeline, including clip metadata and thumbnail images.

**Developed by Daniel Bañuelos**  
🌐 www.dandbc.mx/tools  
☕ Support the project: [buymeacoffee.com/dandbc](https://buymeacoffee.com/dandbc)  
📢 Try before using in professional workflows. Developed using Generative AI.

---

## 📦 Features

- ✅ GUI to select metadata fields, frame capture mode, thumbnail size and filename
- ✅ Exports Excel `.xlsx` with embedded thumbnails and customizable metadata fields
- ✅ Clip color support (via `GetClipColor()`) included
- ✅ Preferred field ordering + automatic fallback to alphabetical
- ✅ Auto-deletes stills from gallery (optional)
- ✅ Persistent user preferences between sessions
- ✅ Cross-platform: tested on macOS & Windows

---

## 🖥 Requirements

- **DaVinci Resolve Studio** (free version does not support scripting API features like `GrabStill()`)
- Python 3.7+ installed on your system if running externally
- The following Python libraries (preinstalled on most systems):
  - `openpyxl`
  - `Pillow`
  - `tkinter` (usually bundled with Python)

To install dependencies manually:

```bash
pip install openpyxl Pillow
```

---

## 📂 Installation

### 🔧 Option 1 – Manual (recommended for most users)

1. Copy the script `DB_Codebook_Generator_v2.2.4_FINAL.py` to your Resolve scripts folder:

#### macOS:
```bash
/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Scripts/Edit/
```

#### Windows:
```bash
C:\ProgramData\Blackmagic Design\DaVinci Resolve\Support\Fusion\Scripts\Edit\
```

2. Restart DaVinci Resolve Studio.

3. In Resolve, go to:
   **Workspace > Scripts > Edit > DB_Codebook_Generator_v2.2.4_FINAL**

---

## 🧪 Usage

1. Open the timeline you want to analyze.
2. Launch the script from Resolve’s menu:
   `Workspace > Scripts > Edit > DB_Codebook_Generator_v2.2.4_FINAL`
3. Use the GUI to:
   - Select metadata fields
   - Choose frame type (first / middle / last)
   - Set thumbnail size
   - Customize filename and timeline start TC
4. The script will:
   - Create a subfolder named after your timeline and project
   - Export a `.xlsx` with embedded thumbnails and metadata
   - Optionally delete stills from the gallery

---

## 📝 Notes & Limitations

- Must be executed from **within DaVinci Resolve Studio**.
- Uses Resolve’s Color page to capture thumbnails — avoid switching pages while it runs.
- Thumbnails and XLSX will be exported into a dedicated subfolder inside your selected folder.
- Clip color may be empty if not assigned in the timeline.
- Supports timeline clips only (non-video or offline clips will be skipped).

---

## 🔭 Roadmap

Planned features for `v2.3` and beyond:

- Drag-and-drop reordering of metadata fields
- Improved UI layout and optional dark mode
- Save/load custom presets
- Batch export across multiple timelines

---

## 💬 Credits

**Script by Daniel Bañuelos**  
🌐 www.dandbc.mx/tools  
☕ [buymeacoffee.com/dandbc](https://buymeacoffee.com/dandbc)  
Feel free to adapt or expand. Attribution appreciated.

---

## ⚠️ Disclaimer

This tool is provided **as-is**. While it has been tested in professional environments, always verify outputs before integrating into production workflows. Developed using Generative AI (ChatGPT-4).

---

## 📄 License

Distributed under the BSD 3-Clause "New" or "Revised" License. See `LICENSE.txt` for full terms.
