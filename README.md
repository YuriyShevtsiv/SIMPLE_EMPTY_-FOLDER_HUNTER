
# 📁 Simple Empty Folder Hunter  
*A lightweight GUI tool for finding and deleting empty folders.*

---

## 📌 Overview  
**Simple Empty Folder Hunter** is a small educational Python application built with **CustomTkinter**.  
It scans a selected directory, finds empty folders (excluding system directories), displays them, and allows the user to delete them with one click.

This project is ideal for beginners learning:

- GUI development with **CustomTkinter**
- File system operations (`os`, `shutil`)
- Basic application structure using classes
- Event‑driven programming

---<img width="770" height="543" alt="Screenshot 2026-03-16 195424" src="https://github.com/user-attachments/assets/fbb2916a-3558-4f53-942e-838045738c6e" />


## 🚀 Features

### 🔍 Scan for Empty Folders
- Recursively scans the selected directory  
- Detects folders with **no files and no subfolders**  
- Skips system directories:
  - `$RECYCLE.BIN`
  - `System Volume Information`

### 🗑️ Delete Empty Folders
- Deletes all found empty folders using `shutil.rmtree`
- Asks for confirmation before deleting
- Shows a summary of how many folders were removed

### 🖥️ Modern GUI
- Built with **CustomTkinter**
- Dark mode enabled by default
- Clean layout with:
  - Folder selection
  - Results display
  - Status bar
  - Action buttons (Scan / Clean All)

---

## 📦 Requirements

Make sure you have:

- Python 3.8+
- The following packages:

```bash
pip install customtkinter
```

*(tkinter is included with most Python installations)*

---

## ▶️ How to Run

1. Download or clone the project.
2. Run the script:

```bash
python simple_folder_hunter.py
```

3. The GUI will open automatically.

---

## 🧭 How to Use

### 1️⃣ Select a Folder  
Click **Select Folder** and choose the directory you want to scan.

### 2️⃣ Scan  
Press **Scan** to search for empty folders.  
Results appear in the central text box.

### 3️⃣ Clean  
Press **Clean All** to delete all detected empty folders.  
You will be asked to confirm before deletion.

---

## 🧩 Code Structure

### `class SimpleFolderHunter(ctk.CTk)`
Main application window.  
Handles UI creation, scanning logic, and folder deletion.

---

### 🔧 Key Methods

| Method | Purpose |
|--------|---------|
| `select_folder()` | Opens folder dialog and stores selected path |
| `scan()` | Runs empty folder search and updates UI |
| `find_empty_folders(start_path)` | Recursively finds empty folders |
| `clean_all()` | Deletes all found empty folders |
| `_show_results(paths)` | Displays results in the text box |
| `_build_ui()` | Builds and arranges all GUI widgets |

---

## 📂 How Empty Folders Are Detected

The method:

```python
for root, dirs, files in os.walk(start_path, topdown=False):
```

walks from the deepest folders upward.

A folder is considered empty if:

- It contains **no files**
- It contains **no non‑ignored subfolders**

This logic ensures that nested empty folders are detected correctly.

---

## ⚠️ Notes & Limitations

- System folders are ignored for safety.
- Deletion uses `shutil.rmtree`, so **deleted folders cannot be restored**.
- The app does not detect folders containing hidden files.

---

## 🏁 Entry Point

At the bottom of the script:

```python
if __name__ == "__main__":
    ctk.set_appearance_mode("dark")
    ctk.set_default_color_theme("blue")
    app = SimpleFolderHunter()
    app.mainloop()
```

This initializes the GUI and starts the event loop.
