# tempcoverter
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        .input-field, .dropdown, .convert-button, .result {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="number"] {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .convert-button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .convert-button:hover {
            background-color: #0056b3;
        }
        .result {
            font-size: 16px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Temperature Converter</h1>
        <div class="input-field">
            <label for="temperature">Degrees</label>
            <input type="number" id="temperature" name="temperature" placeholder="Enter temperature">
        </div>
        <div class="dropdown">
            <label for="unit">Type</label>
            <select id="unit" name="unit">
                <option value="Celsius">Celsius</option>
                <option value="Fahrenheit">Fahrenheit</option>
                <option value="Kelvin">Kelvin</option>
            </select>
        </div>
        <button class="convert-button" onclick="convertTemperature()">Convert</button>
        <div class="result" id="result">Result</div>
    </div>

    <script>
        function convertTemperature() {
            const temperatureInput = document.getElementById('temperature');
            const temperature = parseFloat(temperatureInput.value);
            const unit = document.getElementById('unit').value;

            if (isNaN(temperature)) {
                document.getElementById('result').innerText = 'Please enter a valid number';
                return;
            }

            let resultText = '';

            if (unit === 'Celsius') {
                const fahrenheit = (temperature * 9/5) + 32;
                const kelvin = temperature + 273.15;
                resultText = ${temperature} °C = ${fahrenheit.toFixed(2)} °F = ${kelvin.toFixed(2)} K;
            } else if (unit === 'Fahrenheit') {
                const celsius = (temperature - 32) * 5/9;
                const kelvin = (temperature - 32) * 5/9 + 273.15;
                resultText = ${temperature} °F = ${celsius.toFixed(2)} °C = ${kelvin.toFixed(2)} K;
            } else if (unit === 'Kelvin') {
                const celsius = temperature - 273.15;
                const fahrenheit = (temperature - 273.15) * 9/5 + 32;
                resultText = ${temperature} K = ${celsius.toFixed(2)} °C = ${fahrenheit.toFixed(2)} °F;
            }

            document.getElementById('result').innerText = resultText;
        }
    </script>
</body>
</html>
