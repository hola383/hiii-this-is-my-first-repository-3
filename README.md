import tkinter as tk
import random
import threading
import time

def mover_ventana(ventana):
    while True:
        try:
            x = random.randint(0, 800)
            y = random.randint(0, 600)
            ventana.geometry(f"+{x}+{y}")
            ventana.configure(bg=random.choice(["black"]))
            time.sleep(1)
        except:
            break  # Sale si la ventana se cierra

def crear_ventana():
    ventana = tk.Tk()
    ventana.title("idiot")
    ventana.geometry(f"300x100+{random.randint(0, 800)}+{random.randint(0, 600)}")
    ventana.configure(bg="black")

    mensaje = tk.Label(
        ventana,
        text="you have been hacked idiot :)",
        fg="white",
        bg="black",
        font=("Arial", 10)
    )
    mensaje.pack(expand=True)

    ventana.bind("<Return>", lambda e: ventana.destroy())

    threading.Thread(target=mover_ventana, args=(ventana,), daemon=True).start()
    ventana.mainloop()

for _ in range(20):
    threading.Thread(target=crear_ventana).start()
