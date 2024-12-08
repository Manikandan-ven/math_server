# Ex.05 Design a Website for Server Side Processing
# Date:
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>serverside</title>
    <style>
        
        body {
            display: flex;
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            margin: 0;
            background-color: #e0f7fa;
            flex-direction: column; 
        }

        
        h1 {
            border: 2px solid #009688; 
            padding: 20px;
            margin: 10px;
            border-radius: 5px;
            font-size: xx-large;
            font-weight: bolder;
            font-variant: small-caps;
            background: linear-gradient(to bottom, #009688, #80cbc4); 
            font-family: 'Arial', sans-serif;
            color: white; 
            text-align: center;
            width: 425px; 
            margin-bottom: 20px; 
        }

        
        form {
            border: 2px solid #00796b; 
            background-color: rgba(128, 128, 128, 0.1); 
            padding: 30px;
            margin: 10px;
            border-radius: 10px;
            width: 425px; 
            background-size: 60%;
            background-repeat: no-repeat;
            background-position: left;
            display: flex;
            flex-direction: column;
            align-items: center; 
        }

        
        input[type="text"] {
            padding: 10px;
            margin: 10px 0;
            width: 100%; 
            border-radius: 5px;
            border: 1px solid #009688; 
            background-color: #e0f7fa; 
            color: #00796b; 
        }

        input[type="submit"] {
            padding: 10px 20px;
            background-color: #009688; 
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: #00796b; 
        }
    </style>
</head>
<body>
    <h1>Power of a Lamp Filament</h1>
    <form method="POST">
        {% csrf_token %}
        <div class="power">
            <label for="INTENSITY"><b>INTENSITY:</b></label>
            <input type="text" name="intensity" id="INTENSITY" placeholder="Enter the Value" value="{{i}}">
        </div>
        <br>
        <div class="power">
            <label for="RESISTANCE"><b>RESISTANCE:</b></label>
            <input type="text" name="resistance" id="RESISTANCE" placeholder="Enter the Value" value="{{r}}">
        </div>
        <br>
        <input type="submit" value="CALCULATE">
        <br><br>
        <div class="power">
            <label for="POWER"><b>POWER:</b></label>
            <input type="text" name="POWER" id="POWER" placeholder="Answer" value="{{power}}">
        </div>
    </form>
</body>
</html>

views.py

from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'muni/math.html',context)

    urls.py

    from django.contrib import admin 
from django.urls import path 
from muni import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]

```
# SERVER SIDE PROCESSING:
![Screenshot 2024-12-08 060917](https://github.com/user-attachments/assets/91558f23-5874-4950-ace5-97204e5b2055)

# HOMEPAGE:
![alt text](<Screenshot 2024-12-08 060744-1.png>)
# RESULT:
The program for performing server side processing is completed successfully.
