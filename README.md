# Shotlist Creator & Thumbnail Exporter for DaVinci Resolve

**by Daniel Bañuelos (based on code by Natalia Raz)** | [More tools at dandbc.mx/tools](https://dandbc.mx/tools)

---

## 📋 Overview

This script streamlines the process of creating shotlists and exporting thumbnails directly from **DaVinci Resolve Studio**. It allows editors to:

- Extract markers from the timeline.  
- Capture still frames as thumbnails.  
- Export metadata and images to a comprehensive **Excel (.xlsx)** shotlist.

---

## 🚀 Features

- **Timeline Marker Extraction**: Gathers all markers from the current timeline.  
- **Thumbnail Export**: Captures stills from markers and resizes them for the shotlist.  
- **Metadata Export**: Exports clip metadata (e.g., clip name, timecode, resolution) to Excel.  
- **Customizable Fields**: Choose which metadata fields to include.  
- **User-Friendly UI**: Intuitive interface built with **PySide6** for easy interaction.

---

## 🛠️ Usage

1. Open **DaVinci Resolve Studio** and load your project.  
2. Go to **Keyboard Customization** and assign a key for **“Next Marker”** (*Playback > Next Marker (“0”)*). This setup is required once. If you run `shotlist_creator2.py` directly from DaVinci Resolve Studio, you can modify the hotkey in the script and then assign it in the keyboard customization.  
3. Ensure that the album **stills1** (*in the Color page*) is empty. This is crucial for the script to function correctly.  
4. Run the script. A dialog box will prompt you to select options such as:  
   - Deleting stills from the album on the color page.  
   - Setting the timeline timecode.  
   - Choosing which metadata to extract.  
   - Defining the thumbnail size.  

The script will navigate through the timeline markers, capture thumbnails, and export the marker data and stills to an **Excel** file in your chosen folder.

---

### Running Directly from DaVinci Resolve Studio:

- Copy the file `shotlist_creator2.py` to the **DaVinci Resolve Utility scripts folder**:

  - **For macOS:**  
    `/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Scripts/Utility/`  

  - **For Windows:**  
    `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Fusion\Scripts\Utility\`  

- Ensure the following **Python modules** are installed:

  - `PySide6`  
  - `pynput`  
  - `Pillow`  
  - `xlsxwriter`  
  - `DaVinciResolveScript` (*comes with DaVinci Resolve Studio*)

---

### Additional Tips:

- For annotations, create a **Paint Node** in the **Fusion page** and add your notes there. *Marker annotations and burn-in information will not be exported.*  
- The exported file is optimized for size, making it easy to convert to **PDF** or upload to **Google Sheets**.  
- **macOS Users:**
  - Ensure you grant **Terminal** accessibility access in **Privacy** settings.  
  - It’s recommended to launch **DaVinci Resolve Studio** from `Contents-MacOS-Resolve` for better performance.  
- This script works **only** with the **Studio version** of DaVinci Resolve.  
- Your **feedback** is invaluable! Share your thoughts or suggestions for improving the script. For **user support** or **script modifications**, feel free to reach out.

---

## 📄 Sample Excel Output

The exported **Excel** will include:

- **Marker Information**: Frame number, timecode, notes.  
- **Clip Metadata**: Clip name, resolution, codec, and more.  
- **Thumbnails**: Embedded still images for each marker.

---

## 💡 Notes

- Supports both **Windows** and **macOS**.  
- Uses **PySide6**, **pynput**, and **xlsxwriter** libraries.  
- Ensure **DaVinci Resolve scripting** is properly configured.

---

## 🙏 Acknowledgements

This tool is based on **SHOTLIST CREATOR 2** by **Natalia Raz**. The original script is **donation-based**, so if you find this tool helpful, consider supporting the original creator:

- **Buy on AEscripts**: [aescripts.com/shotlist-creator-for-davinci-resolve/](https://aescripts.com/shotlist-creator-for-davinci-resolve/)  
- **GitHub Repository**: [github.com/natlrazfx/shotlist_creator2](https://github.com/natlrazfx/shotlist_creator2)

---

## ⚖️ Disclaimer

This script was written using **ChatGPT-4o** and adapted by **Daniel Bañuelos**. While care has been taken to ensure functionality, please verify outputs before using them in **critical workflows**.

---

## 👋 About the Author  

**Daniel Bañuelos** — Postproduction Supervisor, Educator, and Tech Enthusiast.  
- **Website:** [dandbc.mx/tools](https://dandbc.mx/tools)  
- **LinkedIn:** [linkedin.com/in/danielbanuelos](https://linkedin.com/in/danielbanuelos)  
- **Email:** dany.b@dandbc.mx  

---

🛠 *Need custom postproduction tools?* — Get in touch via [dany.b@dandbc.mx](mailto:dany.b@dandbc.mx) 🎬🚀
