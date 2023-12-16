import tkinter as tk
from tkinter import scrolledtext, messagebox

def save_note():
    note_content = text_area.get("1.0", tk.END)
    try:
        with open("note.txt", "w") as file:
            file.write(note_content)
        messagebox.showinfo("Note Saved", "Your note has been saved.")
    except Exception as e:
        messagebox.showerror("Error", f"An error occurred: {e}")

def clear_note():
    text_area.delete("1.0", tk.END)

root = tk.Tk()
root.title("Simple Notepad App")

text_area = scrolledtext.ScrolledText(root, wrap=tk.WORD, width=40, height=10)
text_area.pack(padx=10, pady=10)

save_button = tk.Button(root, text="Save Note", command=save_note)
save_button.pack(padx=5, pady=5, side=tk.LEFT)

clear_button = tk.Button(root, text="Clear Note", command=clear_note)
clear_button.pack(padx=5, pady=5, side=tk.RIGHT)

root.mainloop()

