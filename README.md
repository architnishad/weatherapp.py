# weatherapp.py
"""This Weather App is built using Python’s Tkinter library for the graphical user interface (GUI) and the OpenWeatherMap API to fetch real-time weather data.  It allows users to check the current weather conditions, temperature, pressure, and description of any selected location (city or state)"""

from tkinter import *
from tkinter import ttk
import requests

def data_get():
    city = city_name.get().strip()
    if not city:
        return

    # Replace with your valid API key
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid=68418ce436132483c0bce07db5b9f435"
    data = requests.get(url).json()

    if data.get("cod") != 200:
        wc_label1.config(text="N/A")
        wd_label1.config(text="City not found")
        temp_label1.config(text="N/A")
        press_label1.config(text="N/A")
        return

    wc_label1.config(text=data["weather"][0]["main"])
    wd_label1.config(text=data["weather"][0]["description"])
    temp_label1.config(text=f"{data['main']['temp'] - 273.15:.2f} °C")
    press_label1.config(text=f"{data['main']['pressure']} hPa")
in

win = Tk()
win.title("Weather App")
win.config(bg="blue")
win.geometry("500x570")

# Heading
name_label = Label(win, text="Weather App", font=("Times New Roman", 30, "bold"), bg="blue", fg="white")
name_label.place(x=25, y=50, height=50, width=450)

# City Dropdown
city_name = StringVar()
list_name = [   "Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh",
    "Goa", "Gujarat", "Haryana", "Himachal Pradesh", "Jammu and Kashmir",
    "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh", "Maharashtra",
    "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha",
    "Punjab", "Rajasthan", "Sikkim", "Tamil Nadu", "Telangana",
    "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
    "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli",
    "Daman and Diu", "Lakshadweep", "Delhi", "Puducherry"] 

com = ttk.Combobox(win, values=list_name, font=("Times New Roman", 20), textvariable=city_name)
com.place(x=25, y=120, height=50, width=450)

# Weather labels
wc_label = Label(win, text="Weather Climate", font=("Times New Roman", 20), bg="white", fg="black")
wc_label.place(x=25, y=260, height=50, width=210)

wc_label1 = Label(win, text="", font=("Times New Roman", 20))
wc_label1.place(x=250, y=260, height=50, width=210)

wd_label = Label(win, text="Description", font=("Times New Roman", 20), bg="white", fg="black")
wd_label.place(x=25, y=330, height=50, width=210)

wd_label1 = Label(win, text="", font=("Times New Roman", 17))
wd_label1.place(x=250, y=330, height=50, width=210)

temp_label = Label(win, text="Temperature", font=("Times New Roman", 20), bg="white", fg="black")
temp_label.place(x=25, y=400, height=50, width=210)

temp_label1 = Label(win, text="", font=("Times New Roman", 20))
temp_label1.place(x=250, y=400, height=50, width=210)

press_label = Label(win, text="Pressure", font=("Times New Roman", 20), bg="white", fg="black")
press_label.place(x=25, y=470, height=50, width=210)

press_label1 = Label(win, text="", font=("Times New Roman", 20))
press_label1.place(x=250, y=470, height=50, width=210)

# Done button
done_button = Button(win, text="Done", font=("Times New Roman", 20, "bold"), command=data_get)
done_button.place(y=190, height=50, width=100, x=200)

win.mainloop()
