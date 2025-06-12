### ✅ 最新地址：[点丶此丶进丶入](http://a.d44k.cc/17c.html)
<br></br><br></br><br></br><br></br><br></br><br></br>
import tkinter as tk
from tkinter import messagebox

class BuoyancyCalculator:
    def __init__(self, root):
        self.root = root
        self.root.title("简易浮力计算器")
        self.root.geometry("400x300")
        
        # 创建界面元素
        self.create_widgets()
    
    def create_widgets(self):
        # 标题
        title_label = tk.Label(self.root, text="浮力计算器", font=('Arial', 16))
        title_label.pack(pady=10)
        
        # 流体密度输入
        fluid_density_frame = tk.Frame(self.root)
        fluid_density_frame.pack(pady=5)
        
        tk.Label(fluid_density_frame, text="流体密度(kg/m³):").pack(side=tk.LEFT)
        self.fluid_density_entry = tk.Entry(fluid_density_frame)
        self.fluid_density_entry.pack(side=tk.LEFT, padx=5)
        
        # 物体体积输入
        volume_frame = tk.Frame(self.root)
        volume_frame.pack(pady=5)
        
        tk.Label(volume_frame, text="物体体积(m³):").pack(side=tk.LEFT)
        self.volume_entry = tk.Entry(volume_frame)
        self.volume_entry.pack(side=tk.LEFT, padx=5)
        
        # 重力加速度输入
        gravity_frame = tk.Frame(self.root)
        gravity_frame.pack(pady=5)
        
        tk.Label(gravity_frame, text="重力加速度(m/s²):").pack(side=tk.LEFT)
        self.gravity_entry = tk.Entry(gravity_frame)
        self.gravity_entry.insert(0, "9.8")  # 默认值
        self.gravity_entry.pack(side=tk.LEFT, padx=5)
        
        # 计算按钮
        calculate_button = tk.Button(self.root, text="计算浮力", command=self.calculate_buoyancy)
        calculate_button.pack(pady=20)
        
        # 结果显示
        self.result_label = tk.Label(self.root, text="", font=('Arial', 12))
        self.result_label.pack(pady=10)
    
    def calculate_buoyancy(self):
        try:
            # 获取输入值
            fluid_density = float(self.fluid_density_entry.get())
            volume = float(self.volume_entry.get())
            gravity = float(self.gravity_entry.get())
            
            # 计算浮力 (F = ρ * V * g)
            buoyancy = fluid_density * volume * gravity
            
            # 显示结果
            result_text = f"浮力: {buoyancy:.2f} N"
            self.result_label.config(text=result_text, fg="blue")
            
        except ValueError:
            messagebox.showerror("输入错误", "请输入有效的数字")

if __name__ == "__main__":
    root = tk.Tk()
    app = BuoyancyCalculator(root)
    root.mainloop()
