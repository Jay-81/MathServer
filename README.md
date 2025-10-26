# Ex.05 Design a Website for Server Side Processing
## Date:26-10-25

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

math.html
```
<html>
<head>
<style>
body {
  font-size: 20px;
  background-color: #191970; /* Gentler blue */
  margin: 0;
  height: 100vh;
}

.edge {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.box {
  background: white;
  padding: 40px 40px 30px 40px;
  border-radius: 15px;
  box-shadow: 0px 0px 20px #222;
  min-width: 350px;
}

.form1 {
  color: orange;
  text-align: center;
  margin-top: 7px;
  margin-bottom: 6px;
  font-weight: bold;
}

input[type="text"] {
  padding: 7px;
  margin: 4px 0;
  border-radius: 7px;
  border: 1px solid #bbb;
  width: 110px;
  font-size: 18px;
}

input[type="submit"] {
  padding: 7px 20px;
  border-radius: 10px;
  font-size: 18px;
  background: #FF69B4;
  color: white;
  border: none;
  cursor: pointer;
}

h1 {
  color: #FF69B4;
  text-align: center;
  padding-top: 10px;
  margin-top: 0;
  margin-bottom: 25px;
  font-size: 2.1em;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>
</head>

<body>
<div class="edge">
  <div class="box">
    <h1>Area of Rectangle</h1>
    <form method="POST">
      {% csrf_token %}
      <div class="form1">
        Length <input type="text" name="length" value="{{l}}">(in m)<br/>
      </div>
      <div class="form1">
        Breadth <input type="text" name="breadth" value="{{b}}">(in m)<br/>
      </div>
      <div class="form1">
        <input type="submit" value="Calculate"><br/>
      </div>
      <div class="form1">
        Area <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
      </div>
    </form>
  </div>
</div>
</body>
</html>

```
views.py
```
from django.shortcuts import render

def rectarea(request):
    context = {}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"

    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        print('request =', request)
        print('Length =', l)
        print('Breadth =', b)

        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area =', area)

    return render(request, 'mathapp/math.html', context)

```
urls.py

```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/', views.rectarea, name='areaofrectangle'),
    path('', views.rectarea, name='areaofrectangleroot'),
]

```
## SERVER SIDE PROCESSING:

![alt text](<Screenshot (105).png>)

## HOMEPAGE:

![alt text](<Screenshot (104).png>)

## RESULT:
The program for performing server side processing is completed successfully.
