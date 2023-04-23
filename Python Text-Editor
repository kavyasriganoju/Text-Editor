import tkinter as tk
from tkinter import messagebox
from tkinter import filedialog

class Notepad:

    def __init__(self, master):
        self.master = master
        self.master.title("Notepad")
        self.create_widgets()
        self.file_path = None

    def create_widgets(self):
        # Create the text widget
        self.text = tk.Text(self.master)
        self.text.pack(side=tk.LEFT, fill=tk.BOTH, expand=True)

        # Create the scrollbar
        scrollbar = tk.Scrollbar(self.master)
        scrollbar.pack(side=tk.RIGHT, fill=tk.Y)

        # Attach the scrollbar to the text widget
        self.text.config(yscrollcommand=scrollbar.set)
        scrollbar.config(command=self.text.yview)

        # Create the menu bar
        menu_bar = tk.Menu(self.master)
        self.master.config(menu=menu_bar)

        # Create the File menu
        file_menu = tk.Menu(menu_bar, tearoff=False)
        file_menu.add_command(label="New", command=self.new_file)
        file_menu.add_command(label="Open", command=self.open_file)
        file_menu.add_command(label="Save", command=self.save_file)
        file_menu.add_command(label="Save As", command=self.save_file_as)
        file_menu.add_separator()
        file_menu.add_command(label="Exit", command=self.master.quit)
        menu_bar.add_cascade(label="File", menu=file_menu)

        # Create the Help menu
        help_menu = tk.Menu(menu_bar, tearoff=False)
        help_menu.add_command(label="About", command=self.show_about)
        menu_bar.add_cascade(label="Help", menu=help_menu)

    def new_file(self):
        self.text.delete("1.0", tk.END)
        self.file_path = None

    def open_file(self):
        file_path = filedialog.askopenfilename()
        if file_path:
            with open(file_path, "r") as file:
                self.text.delete("1.0", tk.END)
                self.text.insert(tk.END, file.read())
                self.file_path = file_path

    def save_file(self):
        if self.file_path:
            with open(self.file_path, "w") as file:
                file.write(self.text.get("1.0", tk.END))
        else:
            self.save_file_as()

    def save_file_as(self):
        file_path = filedialog.asksaveasfilename()
        if file_path:
            with open(file_path, "w") as file:
                file.write(self.text.get("1.0", tk.END))
                self.file_path = file_path

    def show_about(self):
        messagebox.showinfo("About Notepad", "Notepad - A Simple Text Editor")

root = tk.Tk()
app = Notepad(root)
root.mainloop()
