# Calculadora de Presupuesto Personal

## Descripción
La Calculadora de Presupuesto Personal es una aplicación que ayuda a los usuarios a gestionar sus finanzas de manera sencilla. Permite registrar ingresos y gastos y calcular el saldo mensual disponible. 

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

## Características principales
- Registro de ingresos y gastos con descripciones y categorías:
    - Permite registrar transacciones (ingresos o gastos) con una descripción y categoría personalizada.
    - Los datos se ingresan en una interfaz gráfica sencilla.

- Cálculo automático del saldo disponible:
    - Calcula el saldo en tiempo real restando los gastos totales a los ingresos totales.
    - Muestra el saldo actualizado en la interfaz.

- Almacenamiento en base de datos SQLite:
    - Guarda todas las transacciones en una base de datos local (finanzas.db).
    - Permite consultar y analizar el historial financiero.

- Interfaz gráfica amigable (Tkinter):
    - Usa tkinter para crear una interfaz gráfica fácil de usar.
    - Incluye campos de entrada, botones y etiquetas claras.

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
Instrucciones para ejectuar el codigo:
- Abrir Visual Studio Code
- Guardar el archivo con al extension ```.py ``` con el nombre que prefieras.
- Abrir CMD y navegar hasta la carpeta donde guardaste el archivo
- Ejectuar el script con Python usando el siguiente comando: ```python calculadora_presupuesto.py```
- Por ultimo se abrirá una ventana con la interfaz gráfica de la calculadora de presupuesto donde puedes registrar ingresos y gastos, y verás cómo se actualiza el saldo disponible.

Algunos de los requisitos para usarlo son:
- Python 3.x: Asegúrate de tener Python instalado.
- Tkinter: Viene incluido con Python, no necesitas instalarlo por separado.
- SQLite: También viene incluido con Python.

Un ejemplo de uso:
1. Abre la aplicación.
2. Selecciona el tipo de transacción (Ingreso o Gasto).
3. Ingresa la categoría, descripción y monto.
4. Haz clic en "Agregar Transacción".
5. Verás cómo se actualiza el saldo disponible en la parte inferior.
