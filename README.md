# Ex.05 Design a Website for Server Side Processing
## Date:15.12.2025

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

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Filament Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: palevioletred;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator-container {
            background-color: lightskyblue;
            padding: 2em;
            border-radius: 8px;
            box-shadow: 8px 10px black;
            text-align: center;
        }
        h1 {
            color: #333;
        }
        .form-group {
            margin-bottom: 1em;
            text-align: left;
        }
        .form-group label {
            display: block;
            margin-bottom: 0.5em;
            color: black;
        }
        .form-group input[type="number"] {
            width: 90%;
            padding: 0.8em;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 1em 2em;
            background-color:red;
            color: blue;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
        }
        button:hover {
            background-color:black;
        }
        #result {
            margin-top: 1.5em;
            font-size: 1.2em;
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>

<div class="calculator-container">
    <h1>Incandescent Lamp Filament Power Calculator</h1>
    <div class="form-group">
        <label for="voltage">Voltage (V):</label>
        <input type="number" id="voltage" required>
    </div>
    <div class="form-group">
        <label for="current">Current (A):</label>
        <input type="number" id="current" required>
    </div>
    <button onclick="calculatePower()">Calculate Power</button>
    <p id="result"></p>
</div>

<script>
function calculatePower() {
    // Get the values from the input fields
    const voltage = document.getElementById('voltage').value;
    const current = document.getElementById('current').value;

    // Check if the inputs are valid numbers
    if (voltage === "" || current === "" || isNaN(voltage) || isNaN(current)) {
        document.getElementById('result').innerText = "Please enter valid numbers.";
        return;
    }

    // Calculate the power using P = V * I
    const power = parseFloat(voltage) * parseFloat(current);

    // Display the result
    document.getElementById('result').innerText = `Calculated Power: ${power.toFixed(2)} Watts`;
}
</script>

</body>
</html>



views.py



from django.shortcuts import render

def power_calculator(request):
    
    power = None
    if request.method == 'POST':
        try:
            # Get values from the POST request
            voltage = float(request.POST.get('voltage'))
            current = float(request.POST.get('current'))
            
            # Perform the calculation
            power = voltage * current
            
        except (ValueError, TypeError):
            # Handle invalid input gracefully
            power = "Invalid input"

    # Render the template with the calculation result
    return render(request, 'mathapp/math.html', {'power': power})




urls.py


from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.power_calculator,name="power_calculator"),
   
]

## SERVER SIDE PROCESSING:
<img width="1920" height="964" alt="525727333-b5dbb755-9c80-406c-8828-866ff86aaeff" src="https://github.com/user-attachments/assets/6f992380-a450-4885-8f45-4e10ee341980" />



## HOMEPAGE:
<img width="988" height="482" alt="Screenshot (23)" src="https://github.com/user-attachments/assets/0dcd68e7-3ef2-451a-8592-7935f9406286" />


## RESULT:
The program for performing server side processing is completed successfully.
