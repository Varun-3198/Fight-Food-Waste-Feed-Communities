<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FoodSave - Reduce Food Waste</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2e7d32;
            --primary-light: #4caf50;
            --primary-dark: #1b5e20;
            --secondary: #ff9800;
            --secondary-light: #ffb74d;
            --secondary-dark: #f57c00;
            --text: #333333;
            --text-light: #666666;
            --background: #f5f5f5;
            --card-bg: #ffffff;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --radius: 8px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background-color: white;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }

        .logo i {
            color: var(--secondary);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 25px;
        }

        nav a {
            text-decoration: none;
            color: var(--text);
            font-weight: 500;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--primary);
        }

        .auth-buttons {
            display: flex;
            gap: 15px;
        }

        .btn {
            padding: 8px 16px;
            border-radius: var(--radius);
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            border: none;
        }

        .btn-primary {
            background-color: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--primary-dark);
        }

        .btn-secondary {
            background-color: var(--secondary);
            color: white;
        }

        .btn-secondary:hover {
            background-color: var(--secondary-dark);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        .btn-outline:hover {
            background-color: var(--primary);
            color: white;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('https://images.unsplash.com/photo-1556909114-f6e7ad7d3136?ixlib=rb-4.0.3&auto=format&fit=crop&w=1950&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 100px 0;
            text-align: center;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 20px;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        /* Features Section */
        .features {
            padding: 80px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 50px;
        }

        .section-title h2 {
            font-size: 36px;
            color: var(--primary);
            margin-bottom: 10px;
        }

        .section-title p {
            color: var(--text-light);
            max-width: 600px;
            margin: 0 auto;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .feature-card {
            background-color: var(--card-bg);
            border-radius: var(--radius);
            padding: 30px;
            box-shadow: var(--shadow);
            text-align: center;
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 40px;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .feature-card h3 {
            margin-bottom: 15px;
            color: var(--primary-dark);
        }

        /* Role Selection */
        .roles {
            background-color: var(--primary-light);
            color: white;
            padding: 80px 0;
        }

        .roles .section-title h2 {
            color: white;
        }

        .roles-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .role-card {
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: var(--radius);
            padding: 30px;
            text-align: center;
            backdrop-filter: blur(10px);
            transition: transform 0.3s;
        }

        .role-card:hover {
            transform: translateY(-5px);
        }

        .role-icon {
            font-size: 50px;
            margin-bottom: 20px;
            color: var(--secondary-light);
        }

        .role-card h3 {
            margin-bottom: 15px;
            font-size: 24px;
        }

        /* Dashboard Section */
        .dashboard {
            padding: 80px 0;
            display: none;
        }

        .dashboard.active {
            display: block;
        }

        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .user-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--primary);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            font-weight: bold;
        }

        .dashboard-nav {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 1px solid #ddd;
        }

        .nav-tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
        }

        .nav-tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: 600;
        }

        .dashboard-content {
            background-color: var(--card-bg);
            border-radius: var(--radius);
            padding: 30px;
            box-shadow: var(--shadow);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background-color: var(--background);
            border-radius: var(--radius);
            padding: 20px;
            text-align: center;
        }

        .stat-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 5px;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 14px;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        .data-table th, .data-table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        .data-table th {
            background-color: var(--background);
            font-weight: 600;
        }

        .data-table tr:hover {
            background-color: #f9f9f9;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }

        .form-control {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: var(--radius);
            font-size: 16px;
        }

        .form-row {
            display: flex;
            gap: 20px;
        }

        .form-row .form-group {
            flex: 1;
        }

        /* Footer */
        footer {
            background-color: var(--primary-dark);
            color: white;
            padding: 50px 0 20px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-column h3 {
            margin-bottom: 20px;
            font-size: 20px;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 10px;
        }

        .footer-column a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-column a:hover {
            color: white;
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            transition: background-color 0.3s;
        }

        .social-links a:hover {
            background-color: var(--secondary);
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #ccc;
            font-size: 14px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }

            nav ul {
                gap: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }

            .hero h1 {
                font-size: 36px;
            }

            .hero p {
                font-size: 18px;
            }

            .form-row {
                flex-direction: column;
                gap: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-leaf"></i>
                    <span>FoodSave</span>
                </div>
                <nav>
                    <ul>
                        <li><a href="#home">Home</a></li>
                        <li><a href="#about">About</a></li>
                        <li><a href="#impact">Impact</a></li>
                        <li><a href="#resources">Resources</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </nav>
                <div class="auth-buttons">
                    <button class="btn btn-outline" id="loginBtn">Login</button>
                    <button class="btn btn-primary" id="signupBtn">Sign Up</button>
                </div>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container">
            <h1>Fight Food Waste, Feed Communities</h1>
            <p>Join our platform to reduce food waste, donate surplus food, and help those in need. Together we can make a difference.</p>
            <button class="btn btn-secondary">Get Started</button>
        </div>
    </section>

    <!-- Features Section -->
    <section class="features" id="about">
        <div class="container">
            <div class="section-title">
                <h2>How FoodSave Works</h2>
                <p>Our platform connects food donors with recipient organizations to efficiently redistribute surplus food.</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-utensils"></i>
                    </div>
                    <h3>List Surplus Food</h3>
                    <p>Food donors can easily list surplus food items with details like quantity, type, and expiration date.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-hand-holding-heart"></i>
                    </div>
                    <h3>Coordinate Donations</h3>
                    <p>Our system matches available food with organizations that need it most in your area.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3>Track Impact</h3>
                    <p>Monitor your contribution to reducing food waste and helping communities in real-time.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Role Selection -->
    <section class="roles" id="impact">
        <div class="container">
            <div class="section-title">
                <h2>Join as a...</h2>
                <p>Select your role to get started with FoodSave</p>
            </div>
            <div class="roles-grid">
                <div class="role-card" data-role="donor">
                    <div class="role-icon">
                        <i class="fas fa-store"></i>
                    </div>
                    <h3>Food Donor</h3>
                    <p>Restaurants, supermarkets, and individuals with surplus food to donate.</p>
                </div>
                <div class="role-card" data-role="recipient">
                    <div class="role-icon">
                        <i class="fas fa-hands-helping"></i>
                    </div>
                    <h3>Recipient Organization</h3>
                    <p>Charities, shelters, and food banks that distribute food to those in need.</p>
                </div>
                <div class="role-card" data-role="analyst">
                    <div class="role-icon">
                        <i class="fas fa-chart-bar"></i>
                    </div>
                    <h3>Data Analyst</h3>
                    <p>Track food waste trends, analyze data, and generate efficiency reports.</p>
                </div>
                <div class="role-card" data-role="admin">
                    <div class="role-icon">
                        <i class="fas fa-user-cog"></i>
                    </div>
                    <h3>Admin</h3>
                    <p>Manage platform content, users, and ensure data accuracy.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Dashboard Section (Hidden by default) -->
    <section class="dashboard" id="dashboard">
        <div class="container">
            <div class="dashboard-header">
                <div class="user-info">
                    <div class="user-avatar" id="userAvatar">U</div>
                    <div>
                        <h3 id="userName">User Name</h3>
                        <p id="userRole">Role</p>
                    </div>
                </div>
                <button class="btn btn-outline" id="logoutBtn">Logout</button>
            </div>

            <div class="dashboard-nav">
                <div class="nav-tab active" data-tab="overview">Overview</div>
                <div class="nav-tab" data-tab="food">Food Management</div>
                <div class="nav-tab" data-tab="analytics">Analytics</div>
                <div class="nav-tab" data-tab="settings">Settings</div>
            </div>

            <div class="dashboard-content">
                <!-- Overview Tab -->
                <div class="tab-content active" id="overview">
                    <h2>Dashboard Overview</h2>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-value" id="totalDonations">0</div>
                            <div class="stat-label">Total Donations</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="foodSaved">0 lbs</div>
                            <div class="stat-label">Food Saved</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="peopleFed">0</div>
                            <div class="stat-label">People Fed</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="co2Reduced">0 tons</div>
                            <div class="stat-label">CO₂ Reduced</div>
                        </div>
                    </div>

                    <h3>Recent Activity</h3>
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Activity</th>
                                <th>Status</th>
                                <th>Details</th>
                            </tr>
                        </thead>
                        <tbody id="activityTable">
                            <!-- Activity data will be populated by JavaScript -->
                        </tbody>
                    </table>
                </div>

                <!-- Food Management Tab -->
                <div class="tab-content" id="food">
                    <h2>Food Management</h2>
                    <div class="form-group">
                        <button class="btn btn-primary" id="addFoodBtn">Add New Food Item</button>
                    </div>

                    <h3>Your Food Listings</h3>
                    <table class="data-table">
                        <thead>
                            <tr>
                                <th>Food Item</th>
                                <th>Quantity</th>
                                <th>Expiration</th>
                                <th>Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="foodTable">
                            <!-- Food data will be populated by JavaScript -->
                        </tbody>
                    </table>
                </div>

                <!-- Analytics Tab -->
                <div class="tab-content" id="analytics">
                    <h2>Food Waste Analytics</h2>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-value" id="wasteTrend">-12%</div>
                            <div class="stat-label">Waste Trend</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="efficiency">87%</div>
                            <div class="stat-label">Distribution Efficiency</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="topCategory">Produce</div>
                            <div class="stat-label">Most Donated Category</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="satisfaction">94%</div>
                            <div class="stat-label">Recipient Satisfaction</div>
                        </div>
                    </div>

                    <h3>Monthly Report</h3>
                    <div id="chartPlaceholder" style="height: 300px; background-color: #f9f9f9; display: flex; align-items: center; justify-content: center; border-radius: var(--radius); margin-top: 20px;">
                        <p>Food Distribution Chart Visualization</p>
                    </div>
                </div>

                <!-- Settings Tab -->
                <div class="tab-content" id="settings">
                    <h2>Account Settings</h2>
                    <form id="settingsForm">
                        <div class="form-row">
                            <div class="form-group">
                                <label for="firstName">First Name</label>
                                <input type="text" id="firstName" class="form-control" value="John">
                            </div>
                            <div class="form-group">
                                <label for="lastName">Last Name</label>
                                <input type="text" id="lastName" class="form-control" value="Doe">
                            </div>
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" class="form-control" value="john.doe@example.com">
                        </div>
                        <div class="form-group">
                            <label for="organization">Organization</label>
                            <input type="text" id="organization" class="form-control" value="Green Grocers Inc.">
                        </div>
                        <div class="form-group">
                            <label for="location">Location</label>
                            <input type="text" id="location" class="form-control" value="New York, NY">
                        </div>
                        <button type="submit" class="btn btn-primary">Save Changes</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>FoodSave</h3>
                    <p>Reducing food waste and fighting hunger through technology and community collaboration.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-linkedin-in"></i></a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Quick Links</h3>
                    <ul>
                        <li><a href="#home">Home</a></li>
                        <li><a href="#about">How It Works</a></li>
                        <li><a href="#impact">Our Impact</a></li>
                        <li><a href="#resources">Resources</a></li>
                        <li><a href="#contact">Contact Us</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Resources</h3>
                    <ul>
                        <li><a href="#">Food Safety Guidelines</a></li>
                        <li><a href="#">Donation Best Practices</a></li>
                        <li><a href="#">Impact Reports</a></li>
                        <li><a href="#">Success Stories</a></li>
                        <li><a href="#">FAQ</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Contact Us</h3>
                    <ul>
                        <li><i class="fas fa-map-marker-alt"></i> 123 Green Street, Eco City</li>
                        <li><i class="fas fa-phone"></i> (555) 123-4567</li>
                        <li><i class="fas fa-envelope"></i> info@foodsave.org</li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 FoodSave. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Sample data for demonstration
        const sampleData = {
            donor: {
                name: "Sarah Johnson",
                stats: {
                    totalDonations: 47,
                    foodSaved: "1,250",
                    peopleFed: "3,200",
                    co2Reduced: "2.8"
                },
                activities: [
                    { date: "2023-09-20", activity: "Donated 50 lbs of vegetables", status: "Completed", details: "To City Shelter" },
                    { date: "2023-09-18", activity: "Scheduled pickup for bakery items", status: "Scheduled", details: "Tomorrow, 10 AM" },
                    { date: "2023-09-15", activity: "Donated 30 lbs of fruits", status: "Completed", details: "To Community Kitchen" }
                ],
                foodItems: [
                    { item: "Fresh Vegetables", quantity: "25 lbs", expiration: "2023-09-25", status: "Available" },
                    { item: "Bread & Pastries", quantity: "15 units", expiration: "2023-09-23", status: "Reserved" },
                    { item: "Canned Goods", quantity: "40 cans", expiration: "2024-05-15", status: "Available" }
                ]
            },
            recipient: {
                name: "Community Food Bank",
                stats: {
                    totalDonations: 132,
                    foodSaved: "4,750",
                    peopleFed: "12,500",
                    co2Reduced: "10.2"
                },
                activities: [
                    { date: "2023-09-21", activity: "Received 100 lbs of produce", status: "Completed", details: "From Green Grocers" },
                    { date: "2023-09-19", activity: "Distributed to 5 shelters", status: "Completed", details: "Served 500 people" },
                    { date: "2023-09-16", activity: "Requested dairy products", status: "Pending", details: "Awaiting response" }
                ],
                foodItems: [
                    { item: "Dairy Products", quantity: "Requested", expiration: "N/A", status: "Needed" },
                    { item: "Produce", quantity: "50 lbs", expiration: "2023-09-28", status: "Available" },
                    { item: "Grains", quantity: "30 lbs", expiration: "2024-01-10", status: "Available" }
                ]
            },
            analyst: {
                name: "Alex Chen",
                stats: {
                    totalDonations: "2,847",
                    foodSaved: "68,500",
                    peopleFed: "175,000",
                    co2Reduced: "145.3"
                },
                analytics: {
                    wasteTrend: "-12%",
                    efficiency: "87%",
                    topCategory: "Produce",
                    satisfaction: "94%"
                }
            },
            admin: {
                name: "Admin User",
                stats: {
                    totalDonations: "5,231",
                    foodSaved: "125,000",
                    peopleFed: "312,500",
                    co2Reduced: "260.8"
                }
            }
        };

        // DOM Elements
        const roleCards = document.querySelectorAll('.role-card');
        const dashboard = document.getElementById('dashboard');
        const userAvatar = document.getElementById('userAvatar');
        const userName = document.getElementById('userName');
        const userRole = document.getElementById('userRole');
        const navTabs = document.querySelectorAll('.nav-tab');
        const tabContents = document.querySelectorAll('.tab-content');
        const loginBtn = document.getElementById('loginBtn');
        const signupBtn = document.getElementById('signupBtn');
        const logoutBtn = document.getElementById('logoutBtn');

        // Set initial user role (for demo purposes)
        let currentUserRole = 'donor';

        // Role selection
        roleCards.forEach(card => {
            card.addEventListener('click', () => {
                currentUserRole = card.getAttribute('data-role');
                showDashboard(currentUserRole);
            });
        });

        // Show dashboard for selected role
        function showDashboard(role) {
            dashboard.classList.add('active');
            
            // Update user info based on role
            const userData = sampleData[role];
            userName.textContent = userData.name;
            userRole.textContent = role.charAt(0).toUpperCase() + role.slice(1);
            userAvatar.textContent = userData.name.charAt(0);
            
            // Update stats
            document.getElementById('totalDonations').textContent = userData.stats.totalDonations;
            document.getElementById('foodSaved').textContent = userData.stats.foodSaved + (role === 'analyst' ? '' : ' lbs');
            document.getElementById('peopleFed').textContent = userData.stats.peopleFed;
            document.getElementById('co2Reduced').textContent = userData.stats.co2Reduced + (role === 'analyst' ? '' : ' tons');
            
            // Update activity table
            if (userData.activities) {
                const activityTable = document.getElementById('activityTable');
                activityTable.innerHTML = '';
                userData.activities.forEach(activity => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${activity.date}</td>
                        <td>${activity.activity}</td>
                        <td>${activity.status}</td>
                        <td>${activity.details}</td>
                    `;
                    activityTable.appendChild(row);
                });
            }
            
            // Update food table
            if (userData.foodItems) {
                const foodTable = document.getElementById('foodTable');
                foodTable.innerHTML = '';
                userData.foodItems.forEach(item => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${item.item}</td>
                        <td>${item.quantity}</td>
                        <td>${item.expiration}</td>
                        <td>${item.status}</td>
                        <td>
                            <button class="btn btn-outline" style="padding: 5px 10px; font-size: 14px;">Edit</button>
                            <button class="btn btn-secondary" style="padding: 5px 10px; font-size: 14px;">View</button>
                        </td>
                    `;
                    foodTable.appendChild(row);
                });
            }
            
            // Update analytics if available
            if (userData.analytics) {
                document.getElementById('wasteTrend').textContent = userData.analytics.wasteTrend;
                document.getElementById('efficiency').textContent = userData.analytics.efficiency;
                document.getElementById('topCategory').textContent = userData.analytics.topCategory;
                document.getElementById('satisfaction').textContent = userData.analytics.satisfaction;
            }
            
            // Scroll to dashboard
            dashboard.scrollIntoView({ behavior: 'smooth' });
        }

        // Tab navigation
        navTabs.forEach(tab => {
            tab.addEventListener('click', () => {
                // Remove active class from all tabs
                navTabs.forEach(t => t.classList.remove('active'));
                tabContents.forEach(c => c.classList.remove('active'));
                
                // Add active class to clicked tab
                tab.classList.add('active');
                const tabId = tab.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
            });
        });

        // Login/Signup buttons (demo functionality)
        loginBtn.addEventListener('click', () => {
            alert('Login functionality would be implemented here');
        });

        signupBtn.addEventListener('click', () => {
            alert('Signup functionality would be implemented here');
        });

        // Logout button
        logoutBtn.addEventListener('click', () => {
            dashboard.classList.remove('active');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });

        // Settings form submission
        document.getElementById('settingsForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Settings saved successfully!');
        });

        // Add food button
        document.getElementById('addFoodBtn').addEventListener('click', () => {
            alert('Add new food item form would open here');
        });
    </script>
</body>
</html>
