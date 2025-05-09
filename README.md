# Editorial Codebook Generator for DaVinci Resolve Studio

A DaVinci Resolve Studio script that generates a fully formatted Excel codebook from the current timeline, including clip metadata and thumbnail images.

**Developed by Daniel Bañuelos**  
🌐 www.dandbc.mx/tools  
📢 Try before using in professional workflows. Developed using Generative AI.

---

## 📦 Features

- GUI for selecting metadata fields, thumbnail size, and frame capture point
- Accurate thumbnail sizing in Excel
- Optional deletion of all stills after export
- Customizable filename and organized subfolder creation
- Persistent settings saved between sessions

---

## 🖥 Requirements

- **DaVinci Resolve Studio** (Free version does not support scripting API features like `GrabStill()`)
- Python 3.7 or later installed on your system
- The following Python libraries:
  - `openpyxl`
  - `Pillow` (for image resizing)
  - `tkinter` (usually included with Python)

To install missing dependencies, run:

```bash
pip install openpyxl Pillow
```

---

## 📂 Installation

1. Download the script `DB_Codebook_Generator_v2.py` and place it into:

   ```
   C:\ProgramData\Blackmagic Design\DaVinci Resolve\Fusion\Scripts\Edit\
   ```

2. Restart DaVinci Resolve Studio if it was open.

3. In Resolve, go to the **Edit page**.

4. Open the script from the **Workspace > Scripts** menu. Look for `DB_Codebook_Generator_v2`.

---

## 🧪 Usage

1. Open the timeline you want to analyze.
2. Run the script via `Workspace > Scripts > DB_Codebook_Generator_v2`.
3. Use the GUI to:
   - Select metadata fields
   - Choose thumbnail size and frame capture
   - Set starting timecode
4. Choose the root export folder and customize the output filename (optional).
5. The script will:
   - Create a subfolder with the XLSX and thumbnails
   - Embed thumbnails into the Excel file
   - Save the codebook using your chosen filename

---

## 📝 Notes & Limitations

- Tested with DaVinci Resolve Studio 18+ on Windows.
- Must be run from within Resolve using the scripting menu.
- Uses Resolve’s color page to export thumbnails — do not switch pages while it runs.
- Stills are deleted from the **current still album** if enabled.

---

## 💬 Credits

**Code by Daniel Bañuelos**  
www.dandbc.mx/tools  
Feel free to adapt or expand. Attribution appreciated.

---

## ⚠️ Disclaimer

This tool is provided **as-is**. While it has been tested in professional environments, always verify outputs before integrating into production workflows. Developed using Generative AI (ChatGPT-4).

---

## 📄 License

Distributed under the BSD 3-Clause "New" or "Revised" License. See `LICENSE` file for details.
