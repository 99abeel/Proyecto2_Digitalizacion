# Calculadora de Presupuesto Personal

## Description
The Personal Budget Calculator is an application that helps users manage their finances easily. It allows recording income and expenses and calculates the monthly available balance. 

# Why This Project?

**Problem**:  
Most budgeting tools are either too complex or privacy-invasive.

**Solution**:  
✅ **Simple** Tkinter GUI  
✅ **Private** local SQLite storage  
✅ **Educational** financial visibility  

**Impact**:  
- Helps users avoid overdrafts  
- Teaches budgeting fundamentals  
- 100% offline & lightweight  

--- 

## Main Features
- Income and expense recording with descriptions and categories:
    - Allows recording transactions (income or expenses) with a description and custom category.
    - Data is entered through a simple graphical interface.

- Automatic available balance calculation:
    - Calculates the balance in real time by subtracting total expenses from total income.
    - Displays the updated balance in the interface.

- SQLite database storage:
    - Saves all transactions in a local database (finanzas.db).
    - Allows querying and analyzing financial history.

- User-friendly graphical interface (Tkinter):
    - Uses Tkinter to create an easy-to-use graphical interface.
    - Includes input fields, buttons, and clear labels.

---
## Código del Script
```python
import tkinter as tk
from tkinter import messagebox, ttk
import sqlite3

# Crear la base de datos y la tabla
def crear_base_datos():
    conexion = sqlite3.connect("finanzas.db")
    cursor = conexion.cursor()
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS transacciones (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            tipo TEXT NOT NULL,
            categoria TEXT NOT NULL,
            descripcion TEXT NOT NULL,
            monto REAL NOT NULL,
            fecha TEXT NOT NULL
        )
    ''')
    conexion.commit()
    conexion.close()

# Función para agregar una transacción (ingreso o gasto)
def agregar_transaccion():
    tipo = combo_tipo.get()
    categoria = entry_categoria.get()
    descripcion = entry_descripcion.get()
    monto = float(entry_monto.get())

    if tipo and categoria and descripcion and monto:
        conexion = sqlite3.connect("finanzas.db")
        cursor = conexion.cursor()
        cursor.execute('''
            INSERT INTO transacciones (tipo, categoria, descripcion, monto, fecha)
            VALUES (?, ?, ?, ?, DATE('now'))
        ''', (tipo, categoria, descripcion, monto))
        conexion.commit()
        conexion.close()
        messagebox.showinfo("Éxito", "Transacción agregada correctamente.")
        actualizar_saldo()
        limpiar_campos()
    else:
        messagebox.showwarning("Error", "Por favor, complete todos los campos.")

# Función para calcular el saldo disponible
def calcular_saldo():
    conexion = sqlite3.connect("finanzas.db")
    cursor = conexion.cursor()
    cursor.execute("SELECT SUM(monto) FROM transacciones WHERE tipo = 'Ingreso'")
    ingresos = cursor.fetchone()[0] or 0
    cursor.execute("SELECT SUM(monto) FROM transacciones WHERE tipo = 'Gasto'")
    gastos = cursor.fetchone()[0] or 0
    conexion.close()
    return ingresos - gastos

# Función para actualizar el saldo en la interfaz
def actualizar_saldo():
    saldo = calcular_saldo()
    label_saldo.config(text=f"Saldo disponible: ${saldo:.2f}")

# Función para limpiar los campos de entrada
def limpiar_campos():
    entry_categoria.delete(0, tk.END)
    entry_descripcion.delete(0, tk.END)
    entry_monto.delete(0, tk.END)

# Interfaz gráfica
root = tk.Tk()
root.title("Calculadora de Presupuesto Personal")
root.geometry("400x300")

# Campos de entrada
tk.Label(root, text="Tipo:").grid(row=0, column=0, padx=10, pady=10)
combo_tipo = ttk.Combobox(root, values=["Ingreso", "Gasto"])
combo_tipo.grid(row=0, column=1, padx=10, pady=10)
combo_tipo.current(0)

tk.Label(root, text="Categoría:").grid(row=1, column=0, padx=10, pady=10)
entry_categoria = tk.Entry(root)
entry_categoria.grid(row=1, column=1, padx=10, pady=10)

tk.Label(root, text="Descripción:").grid(row=2, column=0, padx=10, pady=10)
entry_descripcion = tk.Entry(root)
entry_descripcion.grid(row=2, column=1, padx=10, pady=10)

tk.Label(root, text="Monto:").grid(row=3, column=0, padx=10, pady=10)
entry_monto = tk.Entry(root)
entry_monto.grid(row=3, column=1, padx=10, pady=10)

# Botones
tk.Button(root, text="Agregar Transacción", command=agregar_transaccion).grid(row=4, column=0, columnspan=2, pady=10)

# Saldo disponible
label_saldo = tk.Label(root, text="Saldo disponible: $0.00", font=("Arial", 12))
label_saldo.grid(row=5, column=0, columnspan=2, pady=10)

# Iniciar la aplicación
crear_base_datos()
actualizar_saldo()
root.mainloop()
```
Instructions to run the code:
- Open Visual Studio Code
- Save the file with the ```.py``` extension with your preferred name.
- Open CMD and navigate to the folder where you saved the file.
- Run the script with Python using the following command: ```python calculadora_presupuesto.py```
- Finally, a window will open with the budget calculator's graphical interface where you can record income and expenses, and you'll see how the available balance updates.

Some of the requirements to use it are:
- Python 3.x: Make sure you have Python installed.
- Tkinter: Comes included with Python, you don't need to install it separately.
- SQLite: Also comes included with Python.

An example of use:
1. Open the application.
2. Select the transaction type (Income or Expense).
3. Enter the category, description, and amount.
4. Click "Agregar Transacción" (Add Transaction).
5. You'll see how the available balance updates at the bottom.
