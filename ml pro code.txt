import tkinter as tk 
from tkinter import filedialog 
from PIL import Image, ImageTk

root = tk.Tk() 
root.title("Image Resizer and Rotation")
width= root.winfo_screenwidth()               
height= root.winfo_screenheight()               
root.geometry("%dx%d" % (width, height))
root['background']='#856ff8'

def resize_image_window():
    global resize_image_window
    resize_image_window = tk.Toplevel()
    resize_image_window.title("Image Resizer")
    width= resize_image_window.winfo_screenwidth()               
    height= resize_image_window.winfo_screenheight()               
    resize_image_window.geometry("%dx%d" % (width, height))
    resize_image_window['background']='#00FF7F'
    
    # Create GUI components for resize_image_window
    
    resize_image_heading_label = tk. Label(resize_image_window, text="Image Resizer" ,font=('Times 14 underline'),bg='#00BFFF') 
    resize_image_heading_label.place(x=660,y=10)
    
    resize_image_width_label = tk. Label (resize_image_window, text="Width:", relief=tk.SOLID, borderwidth=1)
    resize_image_width_label.place(x=500,y=60)
    global resize_image_width_entry
    resize_image_width_entry = tk.Entry(resize_image_window, relief=tk.SOLID, borderwidth=2)
    resize_image_width_entry.place(x=545,y=60)

    resize_image_height_label = tk. Label(resize_image_window, text="Height:", relief=tk.SOLID, borderwidth=1)
    resize_image_height_label.place(x=700,y=60)
    global resize_image_height_entry
    resize_image_height_entry= tk.Entry(resize_image_window, relief=tk.SOLID, borderwidth=2) 
    resize_image_height_entry.place(x=750,y=60)

    open_and_resize_button = tk.Button(resize_image_window, text="Open and Resize Image", command=open_image_and_resize_image, relief=tk.RAISED, borderwidth=5 )
    open_and_resize_button.place(x=650,y=90)
    
    close_resize_button = tk.Button(resize_image_window, text="Back", command=close_resize_image_window, relief=tk.RAISED, borderwidth=5 )
    close_resize_button.place(x=700,y=600)
    
    resize_image_canvas_label = tk. Label (resize_image_window, text="Before",bg='#FFA500')
    resize_image_canvas_label.place(x=100,y=120)
    global resize_image_canvas
    resize_image_canvas=tk.Canvas(resize_image_window, width=400, height=400, relief=tk.SOLID, borderwidth=2,bg='darkgray')
    resize_image_canvas.place(x=100,y=150)

    resize_image_canvas2_label = tk. Label (resize_image_window, text="After",bg='#FFA500')
    resize_image_canvas2_label.place(x=800,y=120)
    global resize_image_canvas2
    resize_image_canvas2=tk.Canvas(resize_image_window, width=400, height=400, relief=tk.SOLID, borderwidth=2,bg='darkgray')
    resize_image_canvas2.place(x=800,y=150)

def close_resize_image_window():
    resize_image_window.destroy()

def rotate_image_window():
    global rotate_image_window
    rotate_image_window = tk.Toplevel()
    rotate_image_window.title("Image Rotater")
    width= rotate_image_window.winfo_screenwidth()               
    height= rotate_image_window.winfo_screenheight()               
    rotate_image_window.geometry("%dx%d" % (width, height))
    rotate_image_window['background']='#00FF7F'
    
    # Create GUI components for rotate_image_window
    
    rotate_image_heading_label = tk. Label(rotate_image_window, text="Image Rotate" ,font=('Times 14 underline'),bg='#00BFFF') 
    rotate_image_heading_label.place(x=660,y=10)
    
    rotate_image_rotate_label = tk. Label (rotate_image_window, text="Rotating Angle:", relief=tk.SOLID, borderwidth=1)
    rotate_image_rotate_label.place(x=600,y=60)
    global rotate_image_rotate_entry
    rotate_image_rotate_entry = tk.Entry(rotate_image_window, relief=tk.SOLID, borderwidth=2)
    rotate_image_rotate_entry.place(x=700,y=60)
    
    open_and_rotate_button = tk.Button(rotate_image_window, text="Open and Rotate Image", command=open_image_and_rotate_image, relief=tk.RAISED, borderwidth=5)
    open_and_rotate_button.place(x=650,y=90)
    
    close_rotate_button = tk.Button(rotate_image_window, text="Back", command=close_rotate_image_window, relief=tk.RAISED, borderwidth=5 )
    close_rotate_button.place(x=700,y=600)

    rotate_image_canvas_label = tk. Label (rotate_image_window, text="Before",bg='#FFA500')
    rotate_image_canvas_label.place(x=100,y=120)
    global rotate_image_canvas
    rotate_image_canvas=tk.Canvas(rotate_image_window, width=400, height=400, relief=tk.SOLID, borderwidth=2,bg='darkgray')
    rotate_image_canvas.place(x=100,y=150)

    rotate_image_canvas2_label = tk. Label (rotate_image_window, text="After",bg='#FFA500')
    rotate_image_canvas2_label.place(x=800,y=120)
    global rotate_image_canvas2
    rotate_image_canvas2=tk.Canvas(rotate_image_window, width=400, height=400, relief=tk.SOLID, borderwidth=2,bg='darkgray')
    rotate_image_canvas2.place(x=800,y=150)
    
def close_rotate_image_window():
    rotate_image_window.destroy()
    
def open_image_and_resize_image():
    file_path =filedialog.askopenfilename(filetypes=[("Image if file nath:files", ".jpg *.jpeg *.png")])
    if file_path:
        image=Image.open( file_path)
        resize_image_canvas.image = ImageTk.PhotoImage(image) 
        resize_image_canvas.create_image(0, 0, anchor=tk.NW,image=resize_image_canvas.image)
    try:
        width = int(resize_image_width_entry.get())
        height = int(resize_image_height_entry.get())
        image=image.resize((width, height)) 
        resize_image_canvas2.image = ImageTk.PhotoImage(image) 
        resize_image_canvas2.create_image(0, 0, anchor=tk.NW, image=resize_image_canvas2.image)
    except(ValueError, AttributeError, OSError): 
        status_label.configure(text="Invalid dimensions or no image selected.")

def open_image_and_rotate_image():
    file_path =filedialog.askopenfilename(filetypes=[("Image if file nath:files", ".jpg *.jpeg *.png")])
    if file_path:
        image=Image.open( file_path)
        rotate_image_canvas.image = ImageTk.PhotoImage(image) 
        rotate_image_canvas.create_image(0, 0, anchor=tk.NW,image=rotate_image_canvas.image)
    try:
        angle = int(rotate_image_rotate_entry.get())
        image=image.rotate(angle,expand=True) 
        rotate_image_canvas2.image = ImageTk.PhotoImage(image) 
        rotate_image_canvas2.create_image(0, 0, anchor=tk.NW, image=rotate_image_canvas2.image)
    except(ValueError, AttributeError, OSError): 
        status_label.configure(text="Invalid dimensions or no image selected.")

# Create GUI components for root
heading_label = tk. Label(root, text="Hybrid Machine Learning \n Image Processing Project (Resizer and Rotate)" ,font=('Times 14 underline'),bg='#40E0D0') 
heading_label.place(x=550,y=10)

resize_canvas = tk.Canvas(root,height=400,width=400,bg='#856ff8')
resize_canvas.place(x=20,y=150)
img = Image.open("C:\\Users\\harsh\\OneDrive\\Pictures\\Saved Pictures\\Resize.jpg")
resized_img=img.resize((400,400))
resize_canvas.image = ImageTk.PhotoImage(resized_img) 
resize_canvas.create_image(0, 0, anchor=tk.NW,image= resize_canvas.image)

rotate_canvas = tk.Canvas(root,height=400,width=400,bg='#856ff8')
rotate_canvas.place(x=1100,y=150)
img = Image.open("C:\\Users\\harsh\\OneDrive\\Pictures\\Saved Pictures\\Rotate.jpg")
resized_img=img.resize((400,400))
rotate_canvas.image = ImageTk.PhotoImage(resized_img) 
rotate_canvas.create_image(0, 0, anchor=tk.NW,image=rotate_canvas.image)

image_resize_button = tk.Button(root, text="Resize Image", command=resize_image_window, relief=tk.RAISED, borderwidth=5 )
image_resize_button.place(x=680,y=200)

image_rotate_button = tk.Button(root, text="Rotate Image", command=rotate_image_window, relief=tk.RAISED, borderwidth=5)
image_rotate_button.place(x=680,y=270)

status_label = tk. Label(root, text="Error: ",bg='red') 
status_label.place(x=700,y=600)
root.mainloop()