
import tkinter as tk
import subprocess
from tkinter import PhotoImage

class Ventana(tk.Tk):
	def __init__(self):
		super().__init__()
		self.inicializar_gui()

	def inicializar_gui(self):
		self.title("APAGAR PC")
	#	self.geometry("600x200")
		self.resizable(0,0)

		frm_izquierdo=tk.Frame(self,bg="red")
		

		self.imagen=PhotoImage(file="APAGAR2.gif")
		lbl_imagen=tk.Button(frm_izquierdo,image=self.imagen)
		lbl_imagen.grid(row=0,column=1)
		lbl_imagen['command']=self.Apagar_General

		frm_derecho=tk.Frame(self)
		frm_horas=tk.Frame(self)
		frm_minutos=tk.Frame(self)
		frm_minutos_derecho=tk.Frame(self)
		frm_segundos=tk.Frame(self)
		frm_segundos_derecho=tk.Frame(self)

		self.horas1=0
		self.lbl_Horas= tk.Label(frm_derecho,text="0",font=("Verdana",16,"bold"),fg="blue")
		self.lbl_Horas.grid(row=0,column=0)
		btn_Horas_Aumentar=tk.Button(frm_horas,text="Aumentar horas",font=("Verdana",14,"bold"),fg="green")
		btn_Horas_Aumentar['command']=self.Apagar_Horas
		frm_horas.rowconfigure(0,weight=5)
		frm_horas.rowconfigure(1,weight=6)
		frm_horas.rowconfigure(2,weight=7)
		btn_Horas_Aumentar.grid(row=0,column=0,sticky=tk.N,pady=20)
		btn_Horas_Disminuir=tk.Button(frm_horas,text="Disminuir horas",font=("Verdana",14,"bold"),fg="green")
		btn_Horas_Disminuir.grid(row=2,column=0,sticky=tk.S,pady=20)
		btn_Horas_Disminuir['command']=self.Apagar_Disminuir_Horas


		self.minutos1=0
		self.lbl_minutos=tk.Label(frm_minutos,text="0",font=("Verdana",16,"bold"),fg="red")
		self.lbl_minutos.grid(row=0,column=0)
		btn_Minutos_Aumentar=tk.Button(frm_minutos_derecho,text="Aumentar minutos",font=("Verdana",14,"bold"),fg="green")
		btn_Minutos_Aumentar['command']=self.Apagar_Minutos_Aumentar
		frm_minutos.rowconfigure(0,weight=5)
		frm_minutos.rowconfigure(1,weight=6)
		frm_minutos.rowconfigure(2,weight=7)
		btn_Minutos_Aumentar.grid(row=0,column=0, pady=20)
		btn_Minutos_Disminuir=tk.Button(frm_minutos_derecho,text="Disminuir minutos",font=("Verdana",14,"bold"),fg="green")
		btn_Minutos_Disminuir.grid(row=2,column=0, pady=20)
		btn_Minutos_Disminuir['command']=self.Apagar_Minutos_Disminuir

		self.segundos1=0
		self.lbl_segundos=tk.Label(frm_segundos,text="0",font=("Verdana",16,"bold"),fg="brown")
		self.lbl_segundos.grid(row=0,column=0)
		btn_segundos_Aumentar=tk.Button(frm_segundos_derecho,text="Aumentar segundos",font=("Verdana",14,"bold"),fg="green")
		btn_segundos_Aumentar['command']=self.Apagar_segundos_Aumentar
		frm_segundos_derecho.rowconfigure(0,weight=5)
		frm_segundos_derecho.rowconfigure(1,weight=6)
		frm_segundos_derecho.rowconfigure(2,weight=7)
		btn_segundos_Aumentar.grid(row=0,column=0,pady=20)
		btn_segundos_Disminuir=tk.Button(frm_segundos_derecho,text="Disminuir segundos",font=("Verdana",14,"bold"),fg="green")
		btn_segundos_Disminuir.grid(row=2,column=0, pady=20)
		btn_segundos_Disminuir['command']=self.Apagar_segundos_Disminuir

		lbl_marca=tk.Label(frm_segundos_derecho,text="BY: JHOAN BARRERA", font=("Verdana",8,"bold"))
		lbl_marca.grid(row=2,column=1,sticky=tk.S,pady=20,padx=30)
		btn_cancelar_apagado=tk.Button(frm_segundos_derecho,text="CANCELAR APAGADO", font=("Verdana",14,"bold"))
		btn_cancelar_apagado.grid(row=0,column=1,padx=5,pady=5)
		btn_cancelar_apagado['command']=self.cancelar_apagado

		frm_izquierdo.grid(row=0,column=0)
		frm_derecho.grid(row=0,column=1)
		frm_horas.grid(row=0,column=2)
		frm_minutos.grid(row=0,column=3)
		frm_minutos_derecho.grid(row=0,column=4)
		frm_segundos.grid(row=0,column=5)
		frm_segundos_derecho.grid(row=0,column=6)
	#	frm_izquierdo.config(width=520,height=320)
	def Apagar_Horas(self):
		
		self.horas1+=1
		self.lbl_Horas.config(text=self.horas1)

		print(self.horas1)

	def Apagar_Disminuir_Horas(self):
		if self.horas1!=0:
			self.horas1-=1
			self.lbl_Horas.config(text=self.horas1)
			print(self.horas1)

	def Apagar_Minutos_Aumentar(self):
		if self.minutos1==59:
			self.horas1+=1
			self.lbl_Horas.config(text=self.horas1)
			self.minutos1=0
			self.lbl_minutos.config(text=self.minutos1)
		else:
			self.minutos1+=1
			self.lbl_minutos.config(text=self.minutos1)
		print(self.minutos1)
	def Apagar_Minutos_Disminuir(self):
		if self.minutos1!=0:
			self.minutos1-=1
			self.lbl_minutos.config(text=self.minutos1)
		print(self.minutos1)
		
	def Apagar_segundos_Aumentar(self):
		if self.segundos1==59:
			self.minutos1+=1
			self.lbl_minutos.config(text=self.minutos1)
			self.segundos1=0
			self.lbl_segundos.config(text=self.segundos1)
		else:	
			self.segundos1+=1
			self.lbl_segundos.config(text=self.segundos1)
		print(self.segundos1)

	def Apagar_segundos_Disminuir(self):
		if self.segundos1!=0:
			self.segundos1-=1
			self.lbl_segundos.config(text=self.segundos1)
		print(self.segundos1)

	def Apagar_General(self):
		self.multiplicar=(self.horas1*3600)+(self.minutos1*60)+(self.segundos1)
		subprocess.call("shutdown -s -t {}".format(self.multiplicar))
		self.Retroceso()

	def cancelar_apagado(self):
		subprocess.call("shutdown -a")
		self.destroy()

		main()

	def Retroceso(self):
		self.multiplicar-=1

		horas2=int(self.multiplicar/3600)

		minutos2=self.multiplicar-(3600*horas2)
		minutos2=int(minutos2/60)

		segundos2=(60*minutos2)
		segundos2=(self.multiplicar-(3600*horas2))-segundos2
		
		self.lbl_Horas.config(text=horas2)
		self.lbl_minutos.config(text=minutos2)
		self.lbl_segundos.config(text=segundos2)
		print("LOGRADO")
		self.after(1000,self.Retroceso)



def main():
	app=Ventana()
	app.mainloop()

if __name__ == '__main__':
	main()
