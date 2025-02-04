<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dihya Fitness</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        header {
            background-color: #4caf50;
            color: white;
            padding: 20px;
            text-align: center;
        }
        nav {
            display: flex;
            justify-content: center;
            background-color: #333;
        }
        nav a {
            color: white;
            padding: 14px 20px;
            text-decoration: none;
            text-align: center;
        }
        nav a:hover {
            background-color: #4caf50;
        }
        .container {
            padding: 20px;
            text-align: center;
        }
        .service-icons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        .service-icons div {
            background-color: white;
            padding: 30px;
            border-radius: 50%;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            transition: transform 0.3s;
        }
        .service-icons div:hover {
            transform: scale(1.1);
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #333;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
        #calorie-calculator, #trainers, #gyms, #rehab-centers {
            display: none;
        }
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            width: 300px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Dihya Fitness</h1>
        <p>Your partner in health, fitness, and wellness.</p>
    </header>
    <nav>
        <a href="#services">Services</a>
        <a href="#about">About Us</a>
        <a href="#contact">Contact</a>
    </nav>
    <div class="container">
        <section id="services">
            <h2>Our Services</h2>
            <div class="service-icons">
                <div id="calorie-btn">
                    <i class="fas fa-calculator fa-3x"></i>
                    <p>Calorie Calculator</p>
                </div>
                <div id="trainers-btn">
                    <i class="fas fa-dumbbell fa-3x"></i>
                    <p>Personal Trainers</p>
                </div>
                <div id="gyms-btn">
                    <i class="fas fa-store-alt fa-3x"></i>
                    <p>Find Gyms</p>
                </div>
                <div id="rehab-btn">
                    <i class="fas fa-wheelchair fa-3x"></i>
                    <p>Rehabilitation Centers</p>
                </div>
            </div>
        </section>
        
        <section id="about">
            <h2>About Us</h2>
            <p>Diehya Fitness is your comprehensive platform for health and wellness, connecting you with top-tier services and professionals.</p>
        </section>
        <section id="contact">
            <h2>Contact Us</h2>
            <p>Email: support@dihyafitness.com</p>
            <p>Phone: +123 698035602</p>
        </section>
    </div>

    <!-- Modals -->
    <div id="calorie-calculator" class="modal">
        <div class="modal-content">
            <h3>Calorie Calculator</h3>
            <form id="calorie-form">
                <input type="number" id="weight" placeholder="Weight (kg)" required><br>
                <input type="number" id="height" placeholder="Height (cm)" required><br>
                <input type="number" id="age" placeholder="Age" required><br>
                <select id="gender" required>
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                </select><br>
                <select id="activity-level" required>
                    <option value="sedentary">Sedentary</option>
                    <option value="light">Light Activity</option>
                    <option value="moderate">Moderate Activity</option>
                    <option value="active">Active</option>
                </select><br>
                <button type="button" onclick="calculateCalories()">Calculate</button>
            </form>
            <div id="calorie-result"></div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2025 Diehya Fitness. All rights reserved.</p>
    </footer>

    <script>
        // Toggle modals
        document.getElementById('calorie-btn').addEventListener('click', function() {
            document.getElementById('calorie-calculator').style.display = 'flex';
        });

        // Handle modal close (simply click outside modal to close it)
        document.getElementById('calorie-calculator').addEventListener('click', function(e) {
            if (e.target === this) {
                this.style.display = 'none';
            }
        });

        // Function to calculate calories
        function calculateCalories() {
            var weight = parseFloat(document.getElementById('weight').value);
            var height = parseFloat(document.getElementById('height').value);
            var age = parseFloat(document.getElementById('age').value);
            var gender = document.getElementById('gender').value;
            var activityLevel = document.getElementById('activity-level').value;

            var bmr;
            if (gender === 'male') {
                bmr = 10 * weight + 6.25 * height - 5 * age + 5;
            } else {
                bmr = 10 * weight + 6.25 * height - 5 * age - 161;
            }

            var activityMultiplier = {
                'sedentary': 1.2,
                'light': 1.375,
                'moderate': 1.55,
                'active': 1.725
            };

            var dailyCalories = bmr * activityMultiplier[activityLevel];
            document.getElementById('calorie-result').innerText = `Your estimated daily caloric needs are ${Math.round(dailyCalories)} calories.`;
        }
    </script>
</body>
</html>
