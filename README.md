# Alarm-Timer
Real time Clock in IST and alarm timer project 
import tkinter
import winsound
import time
import math
from time import strftime
from tkinter import font as tkfont
from tkinter import Frame
from tkinter import Label

def countdown(count): 
    
    seconds=math.floor(count%60)
    minutes=math.floor((count/60)%60)
    hours=math.floor((count/3600))
    label['text'] ="Hours: "+ str(hours)+ " Minutes:  " +str(minutes)+ " Seconds: " +str(seconds)

    if count >= 0:
        top.after(1000, countdown,count-1)
    else:
        for x in range(6):
         winsound.Beep(1000,1000)
        label['text']="Time is up!"

 
    
def updateButton():
    hour,minute,sec=hoursE.get(),minuteE.get(),secondE.get()
    if hour.isdigit() and minute.isdigit() and sec.isdigit():
        time=int(hour)*3600+int(minute)*60+int(sec)
        countdown(time)
        
top = tkinter.Tk()
top.geometry("640x480")

top.frame = Frame(top)
top.frame.pack(fill = "both")
label = Label(top, text= "Welcome!", font=("Times", 50), bg = "black", fg = "white")
label.pack(side= "top", fill = "both", expand = 1)
top.title_font = tkfont.Font(family = "Times", size = 100, weight = "bold", slant = "italic")
   
def time(): 
    string = strftime('%I:%M:%S %p') 
    lbl.config(text = string) 
    lbl.after(1000, time) 
  
lbl = Label(top, font = ('Times', 52), bg = 'black', fg = 'white') 
lbl.pack(anchor = 'center',fill ="both",expand = 1) 
time() 

hoursT=tkinter.Label(top, text="Hours:")
hoursE=tkinter.Entry(top)
minuteT=tkinter.Label(top, text="Minutes:")
minuteE=tkinter.Entry(top)
secondT=tkinter.Label(top, text="Seconds:")
secondE=tkinter.Entry(top)
hoursT.pack(ipadx=1,ipady=1)
hoursE.pack(ipadx=1,ipady=2)
minuteT.pack(ipadx=2,ipady=1)
minuteE.pack(ipadx=2,ipady=2)
secondT.pack(ipadx=3,ipady=1)
secondE.pack(ipadx=3,ipady=2)
label = tkinter.Label(top)

string = strftime('%H:%M:%S')
label.config(text=string)
label.after(1000, time)
label = Label(top, font = ('Times', 12, 'bold'), bg = 'light grey', fg = 'black')
label.pack()


button=tkinter.Button(top,text="Start Timer",command=updateButton)
button.pack()
top.title(" Alarm Timer ")
top.mainloop()
