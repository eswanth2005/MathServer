# Ex.05 Design a Website for Server Side Processing
## Date: 12.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
```
math.html

<html>
<head>
    <title>Surface Area of a Right Cylinder</title>
    <style>
        h1 {
            color: black;
            text-align: center;
            padding-top: 20px;
        }
        .corner {
            width: 600px;
            height: 250px;
        }

        .outline {
            display: block;
            border: solid;
            height: 300px;
            width: 600px;
            font-size: 20px;
            background-color:orange;
        }

        .inside {
            color: pink;
            text-align: center;
            margin-top: 9px;
            margin-bottom: 6px;
        }

        
    </style>
</head>
<body bgcolor="blue">
    <center>
        <br>
    <div class="corner">
        <div class="outline">
            <h1>Surface Area of Right Cylinder</h1>
            <h5>ESWANTH KUMAR K (212223040046)</h5>
            <form method="POST">
                {% csrf_token %}
                <div class="inside">
                    Radius : <input type="text" name="radius" value="{{r}}"></input>(in m)<br>
                </div>
                <div class="inside">
                    Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br>
                </div>
                <div class="inside">
                    <input type="submit" value="Calculate"></input><br>
                </div>
                <div class="inside">
                    Surface Area : <input type="text" name="area" value="{{area}}"></input> m <sup>2</sup><br>
                </div>
            </form>
        </div>
    </div>
</center>
</body>
</html>

views.py

from django.shortcuts import render
def surfacearea(request):
    context={}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('radius=',r)
        print('height=',h)
        area = 2 * 3.14 * int(r) * int(h) + 2 * 3.14 * int(r) * int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area=',area)
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfaceareaofcylinder/',views.surfacearea,name="surfaceareaofcylinder"),
    path('',views.surfacearea,name="surfaceareaofcylinderroot")
]
```

## SERVER SIDE PROCESSING:

![alt text](<Screenshot (14).png>)

## HOMEPAGE:

![alt text](<Screenshot (12).png>)


## RESULT:
The program for performing server side processing is completed successfully.
