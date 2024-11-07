# Ex.05 Design a Website for Server Side Processing

### Name: Loshini G
### Register No: 212223240008
### Date:

## AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 

## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

### Html.py:
```py
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>Lamp Filament Power Calculator</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
   background-color: rgb(0, 0, 0);
}
.edge {
   width: 100%;
   padding-top: 250px;
   text-align: center;
}
.box {
   display: inline-block;
   width: 500px;
   min-height: 300px;
   font-size: 20px;
   background-color: rgb(57, 58, 58);
}
.formelt {
   color: white;
   text-align: center;
   margin-top: 7px;
   margin-bottom: 6px;
}
h1 {
   color: white;
   padding-top: 20px;
}
</style>
</head>
<h2><center><font color="red">Loshini G 212223240008</font></center></h2> 
<body>
<div class="edge">
   <div class="box">
       <h1>Power of Lamp Filament</h1>
       <form method="POST">
           {% csrf_token %}
           <div class="formelt">
               Intensity (I): <input type="text" name="intensity" value="{{i}}"> A<br/>
           </div>
           <div class="formelt">
               Resistance (R): <input type="text" name="resistance" value="{{r}}"> Ω<br/>
           </div>
           <div class="formelt">
               <input type="submit" value="Calculate"><br/>
           </div>
           <div class="formelt">
               Power (P): <input type="text" name="power" value="{{power}}"> W<br/>
           </div>
       </form>
   </div>
</div>
</body>
</html>
```

### views.py:
```py
from django.shortcuts import render

def calculate_power(request):
    power = None  # Initialize power variable to None to check later if a calculation was made

    if request.method == 'POST':
        try:
            intensity = float(request.POST.get('intensity'))
            resistance = float(request.POST.get('resistance'))

            # Calculate power using the formula P = I^2 * R
            power = intensity**2 * resistance
        except ValueError:
            power = "Invalid input. Please enter numeric values."

    return render(request, 'mathapp/math.html', {'power': power})
```

### urls.py:
**1.**
``` py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.calculate_power, name='calculate_power'),
]
```
**2.**
```py
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('mathapp.urls')),
]
```
## HOMEPAGE:
### Input:
![Screenshot 2024-11-07 110352](https://github.com/user-attachments/assets/beabb3ec-da5d-494e-8039-10270c6432ca)

### Output:
![Screenshot 2024-11-07 110410](https://github.com/user-attachments/assets/06d15024-54ab-49d1-b1ad-f0f7fda70600)

## RESULT:
The program for performing server side processing is completed successfully.
