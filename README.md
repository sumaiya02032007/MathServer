# Ex.05 Design a Website for Server Side Processing
## Date:07/10/2025

## AIM:
To design a website to calculate the Body Mass Index in the server side.


## FORMULA:
```
BMI = W(H/100*2)
BMI --> Body Mass Index
W --> Weight
H --> Height
```
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
math.py

<html>
<head>
<title>Body Mass Index</title>
<style type="text/css">
body {
  font-family: Arial, sans-serif;
  background-color: #67b7c4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  background: rgb(186, 129, 129);
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  width: 350px;
  text-align: center;
}

h1 {
  color: #5c4b4b;
  margin-bottom: 20px;
}

label {
  display: block;
  text-align: left;
  margin: 10px 0 5px;
}

input {
  width: 100%;
  padding: 10px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  background-color: #007BFF;
  color: white;
  border: none;
  padding: 12px;
  border-radius: 5px;
  width: 100%;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

</style>
</head>
<body>
  <div class="edge">
  <div class="box">
  <h1>Body Mass Index</h1>
  <h2>SUMAIYA.S 25016731</h2>
  <form method="POST">
    {% csrf_token %}
  <div class="formelt">
    Weight: <input type="text" name="weight" value="{{w}}"></input>(in kg)<br/>
  </div>
  <div class="formelt">
    Height: <input type="text" name="height" value="{{h}}"></input>(in m)<br/>
  </div>
  <div class="formelt">
    <input type="submit" value="Calculate"></input><br/>
  </div>
  <div class="formelt">
    BMI:<input type="text" name="bmi" value="{{bmi}}"></input>kg/m<sup>2</sup><br/>
  </div>
  </form> 
  </div>
  </div>
</body>
</html> 

 view.py

 from django.shortcuts import render
def bmi(request):
    context={}
    context['bmi']= "0"
    context['w'] = "0"
    context['h']= "0"
    if request.method == 'POST':
        print("POST method is used")
        w = request.POST.get("weight",'0')
        h= request.POST.get("height",'0')
        print('requestt=',request)
        print('Weight=',w)
        print('Height=',h)
        a=float(w)
        b=float(h)
        bmi = a/(b*b)
        context['bmi']=bmi
        context['w']=w
        context['h']=h
        print('BMI=',bmi)
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('bodymassindex/',views.bmi,name="bodymassindex"),
    path('',views.bmi,name="bodymassindexroot")
]

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-05 220530.png>)

## HOMEPAGE:
![alt text](<Screenshot 2025-10-18 074840.png>)

## RESULT:
The program for performing server side processing is completed successfully.
