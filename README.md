# Python-QR-code-convertor-Project
A repository that contains a Python-based project utilising Artificial Intelligence techniques and algorithms. This project aims to explore the capabilities and potential of AI in various applications such as image recognition, natural language processing, and predictive modelling.


import tkinter as tk
from tkinter import filedialog
from tkinter import messagebox
import qrcode

def create_qr_code(data):
    # Create a QR code object
    qr = qrcode.QRCode(version=1, box_size=10, border=5)

    # Add data to the QR code
    qr.add_data(data)

    # Make the QR code
    qr.make(fit=True)

    # Create an image from the QR code
    img = qr.make_image(fill_color="black", back_color="white")

    return img

def on_submit():
    data = entry.get()
    if data:
        try:
            img = create_qr_code(data)
            file_path = filedialog.asksaveasfilename(defaultextension=".png",
                                                    filetypes=[("PNG", "*.png")])
            img.save(file_path)
            messagebox.showinfo("Info", "QR Code saved successfully!")
        except Exception as e:
            messagebox.showerror("Error", e)
    else:
        messagebox.showerror("Error", "Enter Data to create QR code")

root = tk.Tk()
root.title("QR Code Generator")

label = tk.Label(root, text="Enter Data:")
label.pack()

entry = tk.Entry(root)
entry.pack()

submit_button = tk.Button(root, text="Submit", command=on_submit)
submit_button.pack()

root.mainloop()
