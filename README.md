# carbon-footprint-calculator
Carbon Footprint Calculator<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carbon Footprint Calculator</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            padding: 30px 20px;
            color: white;
        }
        
        header h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        header p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .card {
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            padding: 25px;
            margin-bottom: 25px;
        }
        
        .card-title {
            color: #2c3e50;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eee;
            display: flex;
            align-items: center;
        }
        
        .card-title i {
            margin-right: 10px;
            color: #3498db;
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #2c3e50;
        }
        
        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        .input-group input:focus, .input-group select:focus {
            border-color: #3498db;
            outline: none;
        }
        
        .row {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .col {
            flex: 1;
        }
        
        button {
            background: #3498db;
            color: white;
            border: none;
            padding: 15px 25px;
            border-radius: 8px;
            font-size: 18px;
            cursor: pointer;
            transition: background 0.3s;
            display: block;
            width: 100%;
            font-weight: 600;
        }
        
        button:hover {
            background: #2980b9;
        }
        
        .result-container {
            display: none;
            text-align: center;
            padding: 30px;
        }
        
        .carbon-value {
            font-size: 3.5rem;
            font-weight: 700;
            color: #e74c3c;
            margin: 20px 0;
        }
        
        .comparison {
            font-size: 1.2rem;
            margin-bottom: 25px;
            color: #2c3e50;
        }
        
        .suggestions {
            text-align: left;
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .suggestions h3 {
            color: #2c3e50;
            margin-bottom: 15px;
        }
        
        .suggestions ul {
            list-style-type: none;
        }
        
        .suggestions li {
            margin-bottom: 10px;
            padding-left: 25px;
            position: relative;
        }
        
        .suggestions li:before {
            content: "•";
            color: #3498db;
            font-weight: bold;
            position: absolute;
            left: 10px;
        }
        
        .eco-tips {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 30px;
        }
        
        .tip {
            flex: 1;
            min-width: 200px;
            background: #2ecc71;
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        .tip i {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }
        
        .tip h3 {
            margin-bottom: 10px;
        }
        
        footer {
            text-align: center;
            color: white;
            padding: 20px;
            margin-top: 40px;
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .row {
                flex-direction: column;
                gap: 0;
            }
            
            .carbon-value {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Carbon Footprint Calculator</h1>
            <p>Calculate your carbon emissions and discover ways to reduce your environmental impact</p>
        </header>
        
        <div class="card">
            <h2 class="card-title"><i class="fas fa-calculator"></i> Calculate Your Footprint</h2>
            
            <div class="row">
                <div class="col">
                    <div class="input-group">
                        <label for="electricity"><i class="fas fa-bolt"></i> Monthly Electricity Usage (kWh)</label>
                        <input type="number" id="electricity" placeholder="e.g., 200">
                    </div>
                    
                    <div class="input-group">
                        <label for="gas"><i class="fas fa-fire"></i> Natural Gas Usage (therms)</label>
                        <input type="number" id="gas" placeholder="e.g., 50">
                    </div>
                    
                    <div class="input-group">
                        <label for="fuel"><i class="fas fa-gas-pump"></i> Heating Oil Usage (liters)</label>
                        <input type="number" id="fuel" placeholder="e.g., 100">
                    </div>
                </div>
                
                <div class="col">
                    <div class="input-group">
                        <label for="car"><i class="fas fa-car"></i> Car Travel (km per week)</label>
                        <input type="number" id="car" placeholder="e.g., 150">
                    </div>
                    
                    <div class="input-group">
                        <label for="flight"><i class="fas fa-plane"></i> Flight Hours (per year)</label>
                        <input type="number" id="flight" placeholder="e.g., 10">
                    </div>
                    
                    <div class="input-group">
                        <label for="diet"><i class="fas fa-utensils"></i> Dietary Preference</label>
                        <select id="diet">
                            <option value="vegan">Vegan</option>
                            <option value="vegetarian">Vegetarian</option>
                            <option value="mediumMeat">Medium Meat Eater</option>
                            <option value="highMeat">High Meat Eater</option>
                        </select>
                    </div>
                </div>
            </div>
            
            <button id="calculate-btn">Calculate My Carbon Footprint</button>
        </div>
        
        <div class="card result-container" id="result-container">
            <h2 class="card-title"><i class="fas fa-leaf"></i> Your Carbon Footprint</h2>
            
            <p>Your estimated annual carbon footprint is:</p>
            <div class="carbon-value" id="carbon-value">0.00 tons</div>
            
            <p class="comparison" id="comparison"></p>
            
            <div class="suggestions">
                <h3><i class="fas fa-lightbulb"></i> Ways to Reduce Your Footprint</h3>
                <ul id="suggestions-list">
                    <li>Switch to renewable energy sources for your home</li>
                    <li>Use public transportation, bike, or walk when possible</li>
                    <li>Reduce meat consumption and choose local produce</li>
                    <li>Improve home insulation to reduce heating needs</li>
                    <li>Minimize air travel and choose direct flights</li>
                </ul>
            </div>
            
            <div class="eco-tips">
                <div class="tip">
                    <i class="fas fa-sun"></i>
                    <h3>Solar Power</h3>
                    <p>Consider installing solar panels to reduce electricity emissions</p>
                </div>
                
                <div class="tip">
                    <i class="fas fa-bus"></i>
                    <h3>Public Transport</h3>
                    <p>Using public transport can cut your travel emissions by 50%</p>
                </div>
                
                <div class="tip">
                    <i class="fas fa-recycle"></i>
                    <h3>Recycling</h3>
                    <p>Recycling can reduce your waste-related emissions significantly</p>
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <p>Carbon Footprint Calculator | Mini Project | © 2023</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const calculateBtn = document.getElementById('calculate-btn');
            const resultContainer = document.getElementById('result-container');
            const carbonValue = document.getElementById('carbon-value');
            const comparison = document.getElementById('comparison');
            
            calculateBtn.addEventListener('click', function() {
                // Get input values
                const electricity = parseFloat(document.getElementById('electricity').value) || 0;
                const gas = parseFloat(document.getElementById('gas').value) || 0;
                const fuel = parseFloat(document.getElementById('fuel').value) || 0;
                const car = parseFloat(document.getElementById('car').value) || 0;
                const flight = parseFloat(document.getElementById('flight').value) || 0;
                const diet = document.getElementById('diet').value;
                
                // Calculate emissions (simplified calculation)
                const electricityEmissions = electricity * 0.5 * 12; // Monthly to annual
                const gasEmissions = gas * 5.3 * 12; // Monthly to annual
                const fuelEmissions = fuel * 2.68 * 12; // Monthly to annual
                const carEmissions = car * 0.2 * 52; // Weekly to annual
                const flightEmissions = flight * 90; // Per hour
                
                // Diet emissions (tons per year)
                let dietEmissions;
                switch(diet) {
                    case 'vegan':
                        dietEmissions = 1.5;
                        break;
                    case 'vegetarian':
                        dietEmissions = 1.7;
                        break;
                    case 'mediumMeat':
                        dietEmissions = 2.5;
                        break;
                    case 'highMeat':
                        dietEmissions = 3.3;
                        break;
                    default:
                        dietEmissions = 2.0;
                }
                
                // Total emissions in tons
                const totalEmissions = (electricityEmissions + gasEmissions + fuelEmissions + 
                                       carEmissions + flightEmissions) / 1000 + dietEmissions;
                
                // Display result
                carbonValue.textContent = totalEmissions.toFixed(2) + ' tons CO₂ per year';
                
                // Provide comparison
                if (totalEmissions < 4) {
                    comparison.textContent = 'Your carbon footprint is lower than the global average!';
                } else if (totalEmissions < 8) {
                    comparison.textContent = 'Your carbon footprint is around the global average.';
                } else {
                    comparison.textContent = 'Your carbon footprint is higher than the global average.';
                }
                
                // Show result container
                resultContainer.style.display = 'block';
                
                // Scroll to results
                resultContainer.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>
