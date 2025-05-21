# Ex.05 Design a Website for Server Side Processing

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
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: #5f5e60f2;
}
.edge {
    width: 100%;
    padding-top: 180px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed rgb(176, 176, 255);
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: rgb(121, 88, 93);
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 8px;
    margin-bottom: 6px;
}
h1 {
    color: black;
    padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Area of Right Cylinder</h1>
        <h3>Thajesh(212223230229)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}" style="border-radius: 10px;"></input>m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}" style="border-radius: 10px;"></input>m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}" style="border-radius: 10px;">m<sup>2</sup><br/>
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
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html',context)
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfcaearea")
]

```
## SERVER SIDE PROCESSING:
![Screenshot 2024-05-09 084435](https://github.com/dfghytr/MathServer/assets/138970628/462976ac-69e6-4dcc-9da4-4434affc7157)



## OUTPUT:

![Screenshot 2024-05-14 082350](https://github.com/Thajesh2/MathServer/assets/139841959/72537827-e92e-4f23-a612-9459fbe33d6f)



## RESULT:
The program for performing server side processing is completed successfully.
