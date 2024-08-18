import tkinter as tk
from tkinter import messagebox

def calculate_bmi():
    try:
        weight = float(entry_weight.get())
        height_in_inches = float(entry_height.get())
        
        height_in_meters = height_in_inches * 0.0254
        
        bmi = weight / (height_in_meters ** 2)
        bmi = round(bmi, 2)
        
        if bmi < 18.5:
            category = "Underweight"
        elif 18.5 <= bmi < 24.9:
            category = "Normal weight"
        elif 25 <= bmi < 29.9:
            category = "Overweight"
        else:
            category = "Obese"

        result_label.config(text=f"BMI: {bmi}\nCategory: {category}")
    except ValueError:
        messagebox.showerror("Invalid input", "Please enter valid numbers for weight and height.")

root = tk.Tk()
root.title("BMI Calculator")

label_weight = tk.Label(root, text="Enter your weight (kg):")
label_weight.grid(row=0, column=0, padx=10, pady=5)

entry_weight = tk.Entry(root)
entry_weight.grid(row=0, column=1, padx=10, pady=5)

label_height = tk.Label(root, text="Enter your height (inches):")
label_height.grid(row=1, column=0, padx=10, pady=5)

entry_height = tk.Entry(root)
entry_height.grid(row=1, column=1, padx=10, pady=5)
calculate_button = tk.Button(root, text="Calculate BMI", command=calculate_bmi)
calculate_button.grid(row=2, column=0, columnspan=2, pady=10)
result_label = tk.Label(root, text="")
result_label.grid(row=3, column=0, columnspan=2, pady=10)
root.mainloop()
