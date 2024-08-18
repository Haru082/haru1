try:
    import tkinter as tk
    import tkinter.ttk as ttk
    import random
    import pyttsx3
except ImportError:
    import subprocess
    import sys

    def install_package(package):
        subprocess.check_call([sys.executable, "-m", "pip", "install", package])

    try:
        import tkinter as tk
        import tkinter.ttk as ttk
        import random
        import pyttsx3
    except ImportError:
        install_package("tkinter")
        install_package("pyttsx3")
        import tkinter as tk
        import tkinter.ttk as ttk
        import random
        import pyttsx3

# ข้อความภาษาไทย
testi = ["ตามหาฉันสิ!", "ฉันอยู่ที่นี่!", "คุณคลิกที่ไหน?", "อู้ววว, มาหน่อย!", "มันง่ายเกินไป!"]

motore = pyttsx3.init()

class Popup:

    def __init__(self, master):
        self.master = master
        self.popup = tk.Toplevel(master)
        self.popup.title("พยายามจับฉันสิ!")
        self.popup.protocol("WM_DELETE_WINDOW", self.close_popup)

        message_label = ttk.Label(self.popup, text="พยายามจับฉันสิ!", font=("Helvetica", 18, "bold"), foreground="white", background="black")
        message_label.pack(pady=20)

        self.close_button = ttk.Button(self.popup, text="จับแล้ว!", command=self.close_popup)
        self.close_button.pack(pady=10)

        self.popup.style = ttk.Style(self.popup)
        self.popup.style.configure("Popup.TFrame", background="black")
        self.popup.style.configure("TButton", background="white", font=("Helvetica", 14))
        self.popup.style.configure("TLabel", foreground="white", background="black", font=("Helvetica", 14))

        self.popup_frame = ttk.Frame(self.popup, style="Popup.TFrame", width=200)
        self.popup_frame.pack_propagate(0)
        self.popup_frame.pack()

        self.x = random.randint(0, master.winfo_screenwidth() - 200)
        self.y = random.randint(0, master.winfo_screenheight() - 100)
        self.popup.geometry(f"+{self.x}+{self.y}")

    def close_popup(self):
        self.popup.destroy()
        Popup(self.master)
        motore.say(random.choice(testi))
        motore.runAndWait()

root = tk.Tk()
root.withdraw()
popup = Popup(root)
root.mainloop()
