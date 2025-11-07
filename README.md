# weatherapp.py

📖 Description
The Weather App is a simple desktop application built using Python and Tkinter.  
It allows users to check the current weather, temperature, description, and  pressure of any city using the OpenWeatherMap API.

---

🧰 Technologies Used
🐍 Python 3 – Core programming language  
 🖥️ Tkinter – For GUI (Graphical User Interface)  
🌐 Requests – To fetch data from OpenWeatherMap API  
☁️ OpenWeatherMap API – For live weather data  
📦 PyInstaller – Used to convert Python script into an executable `.exe` file  

---

⚙️ Installation & Setup

 1️⃣ Clone the Repository
Bash  
git clone https://github.com/yourusername/weather-app.git 
cd weather-app

2️⃣ Install Dependencies
Bash
pip install requests

3️⃣ Run the Application
Bash
python weather_app.py

4️⃣ Create Executable File
Bash
pyinstaller weather_app.py --onefile

---

🔑 API Setup

1. Visit OpenWeatherMap
2. Create a free account and get your API Key
3. Replace "YOUR_API_KEY" inside the Python code with your actual API key.

---
# 💻 Source Code

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


win = Tk()
win.title("Weather App")
win.config(bg="blue")
win.geometry("500x570")

# Heading
name_label = Label(win, text="Weather App", font=("Times New Roman", 30, "bold"), bg="blue", fg="white")
name_label.place(x=25, y=50, height=50, width=450)

# City Dropdown
city_name = StringVar()
list_name = [
    "Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh",
    "Goa", "Gujarat", "Haryana", "Himachal Pradesh", "Jammu and Kashmir",
    "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh", "Maharashtra",
    "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha",
    "Punjab", "Rajasthan", "Sikkim", "Tamil Nadu", "Telangana",
    "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
    "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli",
    "Daman and Diu", "Lakshadweep", "Delhi", "Puducherry"
]

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


---

📸 Screenshot

![Weather App Screenshot](screenshot.png)

(Add your app screenshot image named screenshot.png in your project folder.)

---

📜 Example Output

City: Delhi  
Weather: Clear  
Temperature: 27°C  
Description: Clear sky  
Pressure: 1013 hPa

---

🧑‍💻 Author

Archit Nishad

📧 Email: architnishad55@gmail.com
🔗GitHub: https://github.com/architnishad/weatherapp.py.git

---

🪪 License

This project is open-source and available under the MIT License.
