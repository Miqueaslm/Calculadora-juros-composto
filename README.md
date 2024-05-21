# Calculadora-juros-composto
import tkinter as tk
from tkinter import messagebox

def calc_juros_compostos(principal, periodo, juros):
    """Calculadora de juros compostos."""
    montante = principal * ((1 + juros/100)**periodo)
    juros = montante - principal
    return montante, juros

def calcular():
    try:
        principal = float(principal_entry.get())
        periodo = float(periodo_entry.get())
        juros = float(juros_entry.get())

        montante, juros = calc_juros_compostos(principal, periodo, juros)
        resultado_label.config(text=f"Montante final: R$ {montante:.2f}\nJuros: R$ {juros:.2f}")
    except ValueError:
        messagebox.showerror("Erro", "Digite valores válidos!")

# Configuração da janela
root = tk.Tk()
root.title("Calculadora de Juros Compostos")

# Campos de entrada
principal_label = tk.Label(root, text="Valor principal (R$):")
principal_entry = tk.Entry(root)
principal_label.pack()
principal_entry.pack()

periodo_label = tk.Label(root, text="Período (dias):")
periodo_entry = tk.Entry(root)
periodo_label.pack()
periodo_entry.pack()

juros_label = tk.Label(root, text="Taxa de juros (%):")
juros_entry = tk.Entry(root)
juros_label.pack()
juros_entry.pack()

# Botão de cálculo
calcular_button = tk.Button(root, text="Calcular", command=calcular)
calcular_button.pack()

# Resultado
resultado_label = tk.Label(root, text="")
resultado_label.pack()

root.mainloop()
