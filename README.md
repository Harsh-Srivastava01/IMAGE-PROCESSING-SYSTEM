# 🖼️ Image Resizer and Rotation Tool (Python Tkinter & Pillow)

A Graphical User Interface (GUI) desktop application built with **Python**, **Tkinter**, and **Pillow (PIL)** for performing dynamic image resizing and spatial rotation with real-time "Before" and "After" canvas previews[cite: 3, 4].

---

## ✨ Features

- **📏 Image Resizing:**
  - Define explicit width and height dimensions in pixels.
  - Load images (`.jpg`, `.jpeg`, `.png`) and resize dynamically.
  - Visual side-by-side comparison between the original and resized output.

- **🔄 Image Rotation:**
  - Input custom rotation angles (e.g., 45°, 90°, 180°)[cite: 4, 5].
  - Expand bounding boxes automatically to prevent clipping during rotation.
  - Side-by-side comparison between original and rotated output[cite: 4, 5].

- **⚠️ Robust Error Handling:**
  - Displays user-friendly error alerts for empty file selections or invalid numerical inputs.

---

## 🛠️ Tech Stack

- **Programming Language:** Python 3.x[cite: 3, 4]
- **GUI Framework:** `tkinter` (Standard Python interface to Tk)[cite: 3, 4]
- **Image Processing Library:** `Pillow` (`PIL.Image`, `PIL.ImageTk`)[cite: 3, 4]

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3 installed on your machine. You will also need the **Pillow** library installed:
bash
pip install pillow

---


## ⚙️ How It Works
1.Main Window (root):Acts as the primary hub offering direct navigation options to either the Resize or Rotate modules.  
2.Resizer Engine:
  * Uses Image.open() to fetch target files via filedialog[cite: 4].
  * Reads inputs from Entry widgets to parse target width and height[cite: 4].
  * Executes image.resize((width, height)) and updates the target Canvas[cite: 4].
3.Rotation Engine:
  *Parses the rotation angle from user input[cite: 4].
  *Executes image.rotate(angle, expand=True) to preserve full frame geometry[cite: 4].

---

👥 Contributors & Acknowledgments
Authors:
  *Harsh Srivastava (Roll No: 2103420100044)  
  *Ritik Kapil (Roll No: 2103420100082)  
Supervised By: Dr. Vijay Kumar Dwivedi (Assistant Professor, UCER)  
Institution: Department of CSE, United College of Engineering and Research, Prayagraj (Affiliated with AKTU Lucknow)  
