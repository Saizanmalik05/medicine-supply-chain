# medicine-supply-chain
blockchain-based medicine supply chain project
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Medicine Supply Chain</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --dark: #1f2937;
            --light: #f9fafb;
            --gray: #9ca3af;
        }

        body {
            background-color: #f3f4f6;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
        }

        .logo i {
            color: var(--secondary);
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .role-badge {
            background-color: var(--primary);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
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
            opacity: 0.9;
        }

        .btn-outline {
            background-color: transparent;
            border: 1px solid var(--primary);
            color: var(--primary);
        }

        .btn-outline:hover {
            background-color: rgba(37, 99, 235, 0.1);
        }

        .btn-danger {
            background-color: var(--danger);
            color: white;
        }

        .btn-danger:hover {
            opacity: 0.9;
        }

        /* Login Page Styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 80vh;
            padding: 20px;
        }

        .login-card {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
            overflow: hidden;
        }

        .login-header {
            background-color: var(--primary);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .login-header h1 {
            font-size: 1.8rem;
            margin-bottom: 5px;
        }

        .login-body {
            padding: 30px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #d1d5db;
            border-radius: 6px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }

        .role-selector {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 10px;
        }

        .role-option {
            border: 2px solid #e5e7eb;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .role-option:hover {
            border-color: var(--primary);
            background-color: rgba(37, 99, 235, 0.05);
        }

        .role-option.selected {
            border-color: var(--primary);
            background-color: rgba(37, 99, 235, 0.1);
        }

        .role-option i {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        /* Dashboard Styles */
        .dashboard {
            display: none;
        }

        .dashboard-header {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }

        .dashboard-header h2 {
            color: var(--dark);
            margin-bottom: 5px;
        }

        .dashboard-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .stat-icon {
            width: 60px;
            height: 60px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
        }

        .stat-icon.manufacturer {
            background-color: rgba(37, 99, 235, 0.1);
            color: var(--primary);
        }

        .stat-icon.distributor {
            background-color: rgba(16, 185, 129, 0.1);
            color: var(--secondary);
        }

        .stat-icon.medical {
            background-color: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .stat-icon.customer {
            background-color: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        .stat-info h3 {
            font-size: 1.8rem;
            margin-bottom: 5px;
        }

        .stat-info p {
            color: var(--gray);
            font-size: 0.9rem;
        }

        .section-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: var(--dark);
            padding-bottom: 10px;
            border-bottom: 2px solid #e5e7eb;
        }

        .medicine-form {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            margin-bottom: 30px;
        }

        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }

        .medicine-list {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            overflow-x: auto;
        }

        .table {
            width: 100%;
            border-collapse: collapse;
        }

        .table th {
            background-color: #f9fafb;
            padding: 15px;
            text-align: left;
            font-weight: 600;
            color: var(--dark);
            border-bottom: 1px solid #e5e7eb;
        }

        .table td {
            padding: 15px;
            border-bottom: 1px solid #e5e7eb;
        }

        .table tr:last-child td {
            border-bottom: none;
        }

        .table tr:hover {
            background-color: #f9fafb;
        }

        .badge {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .badge-success {
            background-color: rgba(16, 185, 129, 0.1);
            color: var(--secondary);
        }

        .badge-warning {
            background-color: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .badge-danger {
            background-color: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        .action-buttons {
            display: flex;
            gap: 10px;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: var(--gray);
            font-size: 0.9rem;
            border-top: 1px solid #e5e7eb;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }

            .role-selector {
                grid-template-columns: 1fr;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .action-buttons {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-pills"></i>
                <span>MediChain</span>
            </div>
            <div class="user-info">
                <div class="role-badge" id="userRole">Not Logged In</div>
                <button class="btn btn-outline" id="logoutBtn">
                    <i class="fas fa-sign-out-alt"></i> Logout
                </button>
            </div>
        </div>
    </header>

    <main class="container">
        <!-- Login Page -->
        <div id="loginPage" class="login-container">
            <div class="login-card">
                <div class="login-header">
                    <h1>Medicine Supply Chain</h1>
                    <p>Role-Based Authentication System</p>
                </div>
                <div class="login-body">
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" id="username" class="form-control" placeholder="Enter your username">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" class="form-control" placeholder="Enter your password">
                    </div>
                    <div class="form-group">
                        <label>Select Your Role</label>
                        <div class="role-selector">
                            <div class="role-option" data-role="manufacturer">
                                <i class="fas fa-industry"></i>
                                <h3>Manufacturer</h3>
                                <p>Create medicines</p>
                            </div>
                            <div class="role-option" data-role="distributor">
                                <i class="fas fa-truck"></i>
                                <h3>Distributor</h3>
                                <p>Transfer medicines</p>
                            </div>
                            <div class="role-option" data-role="medical">
                                <i class="fas fa-clinic-medical"></i>
                                <h3>Medical Store</h3>
                                <p>Sell medicines</p>
                            </div>
                            <div class="role-option" data-role="customer">
                                <i class="fas fa-user"></i>
                                <h3>Customer</h3>
                                <p>Purchase medicines</p>
                            </div>
                        </div>
                    </div>
                    <button class="btn btn-primary" id="loginBtn" style="width: 100%;">
                        <i class="fas fa-sign-in-alt"></i> Login
                    </button>
                </div>
            </div>
        </div>

        <!-- Manufacturer Dashboard -->
        <div id="manufacturerDashboard" class="dashboard">
            <div class="dashboard-header">
                <h2>Manufacturer Dashboard</h2>
                <p>Create new medicines and manage your inventory</p>
            </div>

            <div class="dashboard-stats">
                <div class="stat-card">
                    <div class="stat-icon manufacturer">
                        <i class="fas fa-industry"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="manufacturerMedCount">12</h3>
                        <p>Medicines Created</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon manufacturer">
                        <i class="fas fa-boxes"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="manufacturerStock">450</h3>
                        <p>Total Units in Stock</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon manufacturer">
                        <i class="fas fa-check-circle"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="manufacturerTransferred">8</h3>
                        <p>Medicines Transferred</p>
                    </div>
                </div>
            </div>

            <h3 class="section-title">Add New Medicine</h3>
            <div class="medicine-form">
                <div class="form-row">
                    <div class="form-group">
                        <label for="medName">Medicine Name</label>
                        <input type="text" id="medName" class="form-control" placeholder="Enter medicine name">
                    </div>
                    <div class="form-group">
                        <label for="medBatch">Batch Number</label>
                        <input type="text" id="medBatch" class="form-control" placeholder="Enter batch number">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="medQuantity">Quantity</label>
                        <input type="number" id="medQuantity" class="form-control" placeholder="Enter quantity">
                    </div>
                    <div class="form-group">
                        <label for="medPrice">Price per Unit (₹)</label>
                        <input type="number" id="medPrice" class="form-control" placeholder="Enter price">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="medExpiry">Expiry Date</label>
                        <input type="date" id="medExpiry" class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="medType">Medicine Type</label>
                        <select id="medType" class="form-control">
                            <option value="Tablet">Tablet</option>
                            <option value="Capsule">Capsule</option>
                            <option value="Syrup">Syrup</option>
                            <option value="Injection">Injection</option>
                            <option value="Ointment">Ointment</option>
                        </select>
                    </div>
                </div>
                <button class="btn btn-primary" id="addMedicineBtn">
                    <i class="fas fa-plus-circle"></i> Add Medicine
                </button>
            </div>

            <h3 class="section-title">Your Medicines</h3>
            <div class="medicine-list">
                <table class="table">
                    <thead>
                        <tr>
                            <th>Medicine Name</th>
                            <th>Batch No.</th>
                            <th>Quantity</th>
                            <th>Price (₹)</th>
                            <th>Expiry Date</th>
                            <th>Type</th>
                            <th>Status</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="manufacturerMedTable">
                        <!-- Medicine rows will be inserted here by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Distributor Dashboard -->
        <div id="distributorDashboard" class="dashboard">
            <div class="dashboard-header">
                <h2>Distributor Dashboard</h2>
                <p>Transfer medicines to medical stores</p>
            </div>

            <div class="dashboard-stats">
                <div class="stat-card">
                    <div class="stat-icon distributor">
                        <i class="fas fa-truck"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="distributorReceived">15</h3>
                        <p>Medicines Received</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon distributor">
                        <i class="fas fa-exchange-alt"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="distributorTransferred">9</h3>
                        <p>Medicines Transferred</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon distributor">
                        <i class="fas fa-boxes"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="distributorStock">320</h3>
                        <p>Current Stock</p>
                    </div>
                </div>
            </div>

            <h3 class="section-title">Transfer Medicine to Medical Store</h3>
            <div class="medicine-form">
                <div class="form-row">
                    <div class="form-group">
                        <label for="transferMed">Select Medicine</label>
                        <select id="transferMed" class="form-control">
                            <option value="">Select a medicine to transfer</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="transferQty">Quantity to Transfer</label>
                        <input type="number" id="transferQty" class="form-control" placeholder="Enter quantity">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="medicalStore">Select Medical Store</label>
                        <select id="medicalStore" class="form-control">
                            <option value="store1">City Medical Store</option>
                            <option value="store2">HealthPlus Pharmacy</option>
                            <option value="store3">LifeCare Pharmacy</option>
                            <option value="store4">Wellness Medical</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="transferDate">Transfer Date</label>
                        <input type="date" id="transferDate" class="form-control">
                    </div>
                </div>
                <button class="btn btn-secondary" id="transferMedicineBtn">
                    <i class="fas fa-exchange-alt"></i> Transfer Medicine
                </button>
            </div>

            <h3 class="section-title">Available Medicines for Distribution</h3>
            <div class="medicine-list">
                <table class="table">
                    <thead>
                        <tr>
                            <th>Medicine Name</th>
                            <th>Batch No.</th>
                            <th>Available Qty.</th>
                            <th>Price (₹)</th>
                            <th>Expiry Date</th>
                            <th>Manufacturer</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="distributorMedTable">
                        <!-- Medicine rows will be inserted here by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Medical Store Dashboard -->
        <div id="medicalDashboard" class="dashboard">
            <div class="dashboard-header">
                <h2>Medical Store Dashboard</h2>
                <p>Sell medicines to customers</p>
            </div>

            <div class="dashboard-stats">
                <div class="stat-card">
                    <div class="stat-icon medical">
                        <i class="fas fa-clinic-medical"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="medicalReceived">22</h3>
                        <p>Medicines Received</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon medical">
                        <i class="fas fa-cash-register"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="medicalSold">18</h3>
                        <p>Medicines Sold</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon medical">
                        <i class="fas fa-boxes"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="medicalStock">125</h3>
                        <p>Current Stock</p>
                    </div>
                </div>
            </div>

            <h3 class="section-title">Sell Medicine to Customer</h3>
            <div class="medicine-form">
                <div class="form-row">
                    <div class="form-group">
                        <label for="sellMed">Select Medicine</label>
                        <select id="sellMed" class="form-control">
                            <option value="">Select a medicine to sell</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="sellQty">Quantity to Sell</label>
                        <input type="number" id="sellQty" class="form-control" placeholder="Enter quantity">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="customerName">Customer Name</label>
                        <input type="text" id="customerName" class="form-control" placeholder="Enter customer name">
                    </div>
                    <div class="form-group">
                        <label for="sellDate">Sale Date</label>
                        <input type="date" id="sellDate" class="form-control">
                    </div>
                </div>
                <button class="btn btn-secondary" id="sellMedicineBtn">
                    <i class="fas fa-cash-register"></i> Sell Medicine
                </button>
            </div>

            <h3 class="section-title">Available Medicines in Store</h3>
            <div class="medicine-list">
                <table class="table">
                    <thead>
                        <tr>
                            <th>Medicine Name</th>
                            <th>Batch No.</th>
                            <th>Available Qty.</th>
                            <th>Price (₹)</th>
                            <th>Expiry Date</th>
                            <th>Distributor</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="medicalMedTable">
                        <!-- Medicine rows will be inserted here by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Customer Dashboard -->
        <div id="customerDashboard" class="dashboard">
            <div class="dashboard-header">
                <h2>Customer Dashboard</h2>
                <p>Browse and purchase medicines</p>
            </div>

            <div class="dashboard-stats">
                <div class="stat-card">
                    <div class="stat-icon customer">
                        <i class="fas fa-shopping-cart"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="customerPurchased">7</h3>
                        <p>Medicines Purchased</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon customer">
                        <i class="fas fa-rupee-sign"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="customerSpent">1,850</h3>
                        <p>Total Spent (₹)</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon customer">
                        <i class="fas fa-store"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="customerStores">4</h3>
                        <p>Stores Visited</p>
                    </div>
                </div>
            </div>

            <h3 class="section-title">Available Medicines</h3>
            <div class="medicine-list">
                <table class="table">
                    <thead>
                        <tr>
                            <th>Medicine Name</th>
                            <th>Type</th>
                            <th>Price (₹)</th>
                            <th>Available Qty.</th>
                            <th>Expiry Date</th>
                            <th>Medical Store</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="customerMedTable">
                        <!-- Medicine rows will be inserted here by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>Medicine Supply Chain System &copy; 2023 | Built with Blockchain Technology</p>
            <p>This is a simulation of a blockchain-based medicine tracking system</p>
        </div>
    </footer>

    <script>
        // Application state
        const state = {
            currentUser: null,
            currentRole: null,
            medicines: [
                { id: 1, name: "Paracetamol", batch: "BATCH001", quantity: 100, price: 5, expiry: "2024-12-31", type: "Tablet", status: "Available", owner: "manufacturer" },
                { id: 2, name: "Amoxicillin", batch: "BATCH002", quantity: 50, price: 25, expiry: "2024-10-15", type: "Capsule", status: "Transferred", owner: "distributor" },
                { id: 3, name: "Cetirizine", batch: "BATCH003", quantity: 80, price: 8, expiry: "2025-03-20", type: "Tablet", status: "Available", owner: "manufacturer" },
                { id: 4, name: "Ibuprofen", batch: "BATCH004", quantity: 120, price: 12, expiry: "2024-11-30", type: "Tablet", status: "Transferred", owner: "medical" },
                { id: 5, name: "Vitamin C", batch: "BATCH005", quantity: 200, price: 15, expiry: "2025-06-30", type: "Tablet", status: "Sold", owner: "customer" },
            ],
            transfers: [],
            sales: []
        };

        // DOM Elements
        const loginPage = document.getElementById('loginPage');
        const manufacturerDashboard = document.getElementById('manufacturerDashboard');
        const distributorDashboard = document.getElementById('distributorDashboard');
        const medicalDashboard = document.getElementById('medicalDashboard');
        const customerDashboard = document.getElementById('customerDashboard');
        const userRoleElement = document.getElementById('userRole');
        const logoutBtn = document.getElementById('logoutBtn');
        const loginBtn = document.getElementById('loginBtn');
        const roleOptions = document.querySelectorAll('.role-option');
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');

        // Manufacturer elements
        const addMedicineBtn = document.getElementById('addMedicineBtn');
        const manufacturerMedTable = document.getElementById('manufacturerMedTable');

        // Distributor elements
        const transferMedicineBtn = document.getElementById('transferMedicineBtn');
        const distributorMedTable = document.getElementById('distributorMedTable');
        const transferMedSelect = document.getElementById('transferMed');

        // Medical store elements
        const sellMedicineBtn = document.getElementById('sellMedicineBtn');
        const medicalMedTable = document.getElementById('medicalMedTable');
        const sellMedSelect = document.getElementById('sellMed');

        // Customer elements
        const customerMedTable = document.getElementById('customerMedTable');

        // Initialize the application
        document.addEventListener('DOMContentLoaded', function() {
            // Check if user is already logged in
            const savedUser = localStorage.getItem('medchain_user');
            const savedRole = localStorage.getItem('medchain_role');
            
            if (savedUser && savedRole) {
                state.currentUser = savedUser;
                state.currentRole = savedRole;
                showDashboard(savedRole);
            }

            // Event listeners for role selection
            roleOptions.forEach(option => {
                option.addEventListener('click', function() {
                    // Remove selected class from all options
                    roleOptions.forEach(opt => opt.classList.remove('selected'));
                    // Add selected class to clicked option
                    this.classList.add('selected');
                });
            });

            // Login button event
            loginBtn.addEventListener('click', handleLogin);

            // Logout button event
            logoutBtn.addEventListener('click', handleLogout);

            // Manufacturer events
            addMedicineBtn.addEventListener('click', addMedicine);

            // Distributor events
            transferMedicineBtn.addEventListener('click', transferMedicine);

            // Medical store events
            sellMedicineBtn.addEventListener('click', sellMedicine);

            // Initialize medicine tables
            updateMedicineTables();
            
            // Set default dates
            setDefaultDates();
        });

        // Set default dates for forms
        function setDefaultDates() {
            const today = new Date().toISOString().split('T')[0];
            const nextYear = new Date();
            nextYear.setFullYear(nextYear.getFullYear() + 1);
            const nextYearStr = nextYear.toISOString().split('T')[0];
            
            // Set default expiry date to next year
            document.getElementById('medExpiry').value = nextYearStr;
            document.getElementById('transferDate').value = today;
            document.getElementById('sellDate').value = today;
        }

        // Handle login
        function handleLogin() {
            const username = usernameInput.value.trim();
            const password = passwordInput.value.trim();
            const selectedRole = document.querySelector('.role-option.selected');
            
            if (!username || !password) {
                alert('Please enter username and password');
                return;
            }
            
            if (!selectedRole) {
                alert('Please select a role');
                return;
            }
            
            const role = selectedRole.getAttribute('data-role');
            
            // Simple authentication (in a real app, this would connect to a backend)
            state.currentUser = username;
            state.currentRole = role;
            
            // Save to localStorage
            localStorage.setItem('medchain_user', username);
            localStorage.setItem('medchain_role', role);
            
            // Show dashboard for the selected role
            showDashboard(role);
            
            // Update UI
            userRoleElement.textContent = `${role.charAt(0).toUpperCase() + role.slice(1)}: ${username}`;
        }

        // Handle logout
        function handleLogout() {
            state.currentUser = null;
            state.currentRole = null;
            
            // Clear localStorage
            localStorage.removeItem('medchain_user');
            localStorage.removeItem('medchain_role');
            
            // Show login page and hide all dashboards
            loginPage.style.display = 'flex';
            manufacturerDashboard.style.display = 'none';
            distributorDashboard.style.display = 'none';
            medicalDashboard.style.display = 'none';
            customerDashboard.style.display = 'none';
            
            // Reset form
            usernameInput.value = '';
            passwordInput.value = '';
            roleOptions.forEach(opt => opt.classList.remove('selected'));
            
            // Update UI
            userRoleElement.textContent = 'Not Logged In';
        }

        // Show dashboard based on role
        function showDashboard(role) {
            // Hide login page
            loginPage.style.display = 'none';
            
            // Hide all dashboards
            manufacturerDashboard.style.display = 'none';
            distributorDashboard.style.display = 'none';
            medicalDashboard.style.display = 'none';
            customerDashboard.style.display = 'none';
            
            // Show the appropriate dashboard
            if (role === 'manufacturer') {
                manufacturerDashboard.style.display = 'block';
                updateManufacturerStats();
                populateManufacturerTable();
            } else if (role === 'distributor') {
                distributorDashboard.style.display = 'block';
                updateDistributorStats();
                populateDistributorTable();
                populateTransferMedSelect();
            } else if (role === 'medical') {
                medicalDashboard.style.display = 'block';
                updateMedicalStats();
                populateMedicalTable();
                populateSellMedSelect();
            } else if (role === 'customer') {
                customerDashboard.style.display = 'block';
                updateCustomerStats();
                populateCustomerTable();
            }
        }

        // Add new medicine (Manufacturer function)
        function addMedicine() {
            const name = document.getElementById('medName').value.trim();
            const batch = document.getElementById('medBatch').value.trim();
            const quantity = parseInt(document.getElementById('medQuantity').value);
            const price = parseInt(document.getElementById('medPrice').value);
            const expiry = document.getElementById('medExpiry').value;
            const type = document.getElementById('medType').value;
            
            // Validation
            if (!name || !batch || !quantity || !price || !expiry) {
                alert('Please fill all fields');
                return;
            }
            
            if (quantity <= 0 || price <= 0) {
                alert('Quantity and price must be positive numbers');
                return;
            }
            
            // Create new medicine object
            const newMedicine = {
                id: state.medicines.length + 1,
                name: name,
                batch: batch,
                quantity: quantity,
                price: price,
                expiry: expiry,
                type: type,
                status: "Available",
                owner: "manufacturer"
            };
            
            // Add to state
            state.medicines.push(newMedicine);
            
            // Update UI
            updateMedicineTables();
            updateManufacturerStats();
            populateManufacturerTable();
            
            // Reset form
            document.getElementById('medName').value = '';
            document.getElementById('medBatch').value = '';
            document.getElementById('medQuantity').value = '';
            document.getElementById('medPrice').value = '';
            
            // Show success message
            alert(`Medicine "${name}" added successfully!`);
            
            // Log the action (simulating smart contract function)
            console.log(`Smart Contract: addMedicine("${name}", "${batch}", ${quantity}, ${price}, "${expiry}", "${type}")`);
        }

        // Transfer medicine (Distributor function)
        function transferMedicine() {
            const medId = parseInt(transferMedSelect.value);
            const quantity = parseInt(document.getElementById('transferQty').value);
            const store = document.getElementById('medicalStore').value;
            const date = document.getElementById('transferDate').value;
            
            // Validation
            if (!medId || !quantity || !store || !date) {
                alert('Please fill all fields');
                return;
            }
            
            if (quantity <= 0) {
                alert('Quantity must be a positive number');
                return;
            }
            
            // Find the medicine
            const medicine = state.medicines.find(m => m.id === medId);
            
            if (!medicine) {
                alert('Medicine not found');
                return;
            }
            
            if (medicine.quantity < quantity) {
                alert(`Insufficient stock. Available: ${medicine.quantity}`);
                return;
            }
            
            // Update medicine quantity and owner
            medicine.quantity -= quantity;
            
            // If quantity becomes 0, mark as transferred
            if (medicine.quantity === 0) {
                medicine.status = "Transferred";
            }
            
            // Create a new medicine entry for the medical store
            const newMedicine = {
                id: state.medicines.length + 1,
                name: medicine.name,
                batch: medicine.batch,
                quantity: quantity,
                price: medicine.price * 1.2, // 20% markup for medical store
                expiry: medicine.expiry,
                type: medicine.type,
                status: "Available",
                owner: "medical"
            };
            
            state.medicines.push(newMedicine);
            
            // Record the transfer
            state.transfers.push({
                medicineId: medId,
                medicineName: medicine.name,
                quantity: quantity,
                from: "Distributor",
                to: store,
                date: date
            });
            
            // Update UI
            updateMedicineTables();
            updateDistributorStats();
            populateDistributorTable();
            populateTransferMedSelect();
            
            // Reset form
            document.getElementById('transferQty').value = '';
            
            // Show success message
            alert(`Transferred ${quantity} units of "${medicine.name}" to ${store}`);
            
            // Log the action (simulating smart contract function)
            console.log(`Smart Contract: transferMedicine(${medId}, ${quantity}, "${store}", "${date}")`);
        }

        // Sell medicine (Medical store function)
        function sellMedicine() {
            const medId = parseInt(sellMedSelect.value);
            const quantity = parseInt(document.getElementById('sellQty').value);
            const customer = document.getElementById('customerName').value.trim();
            const date = document.getElementById('sellDate').value;
            
            // Validation
            if (!medId || !quantity || !customer || !date) {
                alert('Please fill all fields');
                return;
            }
            
            if (quantity <= 0) {
                alert('Quantity must be a positive number');
                return;
            }
            
            // Find the medicine
            const medicine = state.medicines.find(m => m.id === medId);
            
            if (!medicine) {
                alert('Medicine not found');
                return;
            }
            
            if (medicine.quantity < quantity) {
                alert(`Insufficient stock. Available: ${medicine.quantity}`);
                return;
            }
            
            // Update medicine quantity
            medicine.quantity -= quantity;
            
            // If quantity becomes 0, mark as sold
            if (medicine.quantity === 0) {
                medicine.status = "Sold";
            }
            
            // Create a new medicine entry for the customer
            const newMedicine = {
                id: state.medicines.length + 1,
                name: medicine.name,
                batch: medicine.batch,
                quantity: quantity,
                price: medicine.price * 1.1, // 10% markup for customer
                expiry: medicine.expiry,
                type: medicine.type,
                status: "Sold",
                owner: "customer"
            };
            
            state.medicines.push(newMedicine);
            
            // Record the sale
            state.sales.push({
                medicineId: medId,
                medicineName: medicine.name,
                quantity: quantity,
                price: medicine.price,
                total: medicine.price * quantity,
                customer: customer,
                date: date
            });
            
            // Update UI
            updateMedicineTables();
            updateMedicalStats();
            populateMedicalTable();
            populateSellMedSelect();
            
            // Reset form
            document.getElementById('sellQty').value = '';
            document.getElementById('customerName').value = '';
            
            // Show success message
            alert(`Sold ${quantity} units of "${medicine.name}" to ${customer} for ₹${medicine.price * quantity}`);
            
            // Log the action (simulating smart contract function)
            console.log(`Smart Contract: sellMedicine(${medId}, ${quantity}, "${customer}", "${date}")`);
        }

        // Update all medicine tables
        function updateMedicineTables() {
            populateManufacturerTable();
            populateDistributorTable();
            populateMedicalTable();
            populateCustomerTable();
        }

        // Populate manufacturer medicine table
        function populateManufacturerTable() {
            manufacturerMedTable.innerHTML = '';
            
            const manufacturerMeds = state.medicines.filter(m => m.owner === "manufacturer");
            
            manufacturerMeds.forEach(med => {
                const row = document.createElement('tr');
                
                let statusClass = 'badge-success';
                if (med.status === "Transferred") statusClass = 'badge-warning';
                if (med.status === "Sold") statusClass = 'badge-danger';
                
                row.innerHTML = `
                    <td>${med.name}</td>
                    <td>${med.batch}</td>
                    <td>${med.quantity}</td>
                    <td>${med.price}</td>
                    <td>${med.expiry}</td>
                    <td>${med.type}</td>
                    <td><span class="badge ${statusClass}">${med.status}</span></td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn btn-outline btn-sm" onclick="transferMedicineFromManufacturer(${med.id})">
                                <i class="fas fa-exchange-alt"></i> Transfer
                            </button>
                        </div>
                    </td>
                `;
                
                manufacturerMedTable.appendChild(row);
            });
        }

        // Populate distributor medicine table
        function populateDistributorTable() {
            distributorMedTable.innerHTML = '';
            
            const distributorMeds = state.medicines.filter(m => m.owner === "distributor" || (m.owner === "manufacturer" && m.status === "Transferred"));
            
            distributorMeds.forEach(med => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${med.name}</td>
                    <td>${med.batch}</td>
                    <td>${med.quantity}</td>
                    <td>${med.price}</td>
                    <td>${med.expiry}</td>
                    <td>MediPharma Corp.</td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn btn-secondary btn-sm" onclick="selectMedicineForTransfer(${med.id})">
                                <i class="fas fa-truck"></i> Transfer
                            </button>
                        </div>
                    </td>
                `;
                
                distributorMedTable.appendChild(row);
            });
        }

        // Populate medical store medicine table
        function populateMedicalTable() {
            medicalMedTable.innerHTML = '';
            
            const medicalMeds = state.medicines.filter(m => m.owner === "medical");
            
            medicalMeds.forEach(med => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${med.name}</td>
                    <td>${med.batch}</td>
                    <td>${med.quantity}</td>
                    <td>${med.price}</td>
                    <td>${med.expiry}</td>
                    <td>Health Distributors</td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn btn-secondary btn-sm" onclick="selectMedicineForSelling(${med.id})">
                                <i class="fas fa-cash-register"></i> Sell
                            </button>
                        </div>
                    </td>
                `;
                
                medicalMedTable.appendChild(row);
            });
        }

        // Populate customer medicine table
        function populateCustomerTable() {
            customerMedTable.innerHTML = '';
            
            const customerMeds = state.medicines.filter(m => m.owner === "medical" && m.quantity > 0);
            
            customerMeds.forEach(med => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${med.name}</td>
                    <td>${med.type}</td>
                    <td>${med.price}</td>
                    <td>${med.quantity}</td>
                    <td>${med.expiry}</td>
                    <td>City Medical Store</td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn btn-primary btn-sm" onclick="purchaseMedicine(${med.id})">
                                <i class="fas fa-shopping-cart"></i> Purchase
                            </button>
                        </div>
                    </td>
                `;
                
                customerMedTable.appendChild(row);
            });
        }

        // Populate transfer medicine select (distributor)
        function populateTransferMedSelect() {
            transferMedSelect.innerHTML = '<option value="">Select a medicine to transfer</option>';
            
            const availableMeds = state.medicines.filter(m => m.owner === "distributor" || (m.owner === "manufacturer" && m.status === "Transferred"));
            
            availableMeds.forEach(med => {
                const option = document.createElement('option');
                option.value = med.id;
                option.textContent = `${med.name} (Batch: ${med.batch}, Available: ${med.quantity})`;
                transferMedSelect.appendChild(option);
            });
        }

        // Populate sell medicine select (medical store)
        function populateSellMedSelect() {
            sellMedSelect.innerHTML = '<option value="">Select a medicine to sell</option>';
            
            const availableMeds = state.medicines.filter(m => m.owner === "medical" && m.quantity > 0);
            
            availableMeds.forEach(med => {
                const option = document.createElement('option');
                option.value = med.id;
                option.textContent = `${med.name} (Batch: ${med.batch}, Available: ${med.quantity})`;
                sellMedSelect.appendChild(option);
            });
        }

        // Update manufacturer statistics
        function updateManufacturerStats() {
            const manufacturerMeds = state.medicines.filter(m => m.owner === "manufacturer");
            const totalMedicines = manufacturerMeds.length;
            const totalStock = manufacturerMeds.reduce((sum, med) => sum + med.quantity, 0);
            const transferredMeds = manufacturerMeds.filter(m => m.status === "Transferred").length;
            
            document.getElementById('manufacturerMedCount').textContent = totalMedicines;
            document.getElementById('manufacturerStock').textContent = totalStock;
            document.getElementById('manufacturerTransferred').textContent = transferredMeds;
        }

        // Update distributor statistics
        function updateDistributorStats() {
            const distributorMeds = state.medicines.filter(m => m.owner === "distributor" || (m.owner === "manufacturer" && m.status === "Transferred"));
            const receivedMeds = distributorMeds.length;
            const transferredMeds = state.transfers.length;
            const totalStock = distributorMeds.reduce((sum, med) => sum + med.quantity, 0);
            
            document.getElementById('distributorReceived').textContent = receivedMeds;
            document.getElementById('distributorTransferred').textContent = transferredMeds;
            document.getElementById('distributorStock').textContent = totalStock;
        }

        // Update medical store statistics
        function updateMedicalStats() {
            const medicalMeds = state.medicines.filter(m => m.owner === "medical");
            const receivedMeds = medicalMeds.length;
            const soldMeds = state.sales.length;
            const totalStock = medicalMeds.reduce((sum, med) => sum + med.quantity, 0);
            
            document.getElementById('medicalReceived').textContent = receivedMeds;
            document.getElementById('medicalSold').textContent = soldMeds;
            document.getElementById('medicalStock').textContent = totalStock;
        }

        // Update customer statistics
        function updateCustomerStats() {
            const customerMeds = state.medicines.filter(m => m.owner === "customer");
            const purchasedMeds = customerMeds.length;
            const totalSpent = customerMeds.reduce((sum, med) => sum + (med.price * med.quantity), 0);
            const storesVisited = 4; // Hardcoded for demo
            
            document.getElementById('customerPurchased').textContent = purchasedMeds;
            document.getElementById('customerSpent').textContent = totalSpent.toLocaleString();
            document.getElementById('customerStores').textContent = storesVisited;
        }

        // Helper functions for UI interactions
        function selectMedicineForTransfer(medId) {
            transferMedSelect.value = medId;
            transferMedSelect.dispatchEvent(new Event('change'));
        }

        function selectMedicineForSelling(medId) {
            sellMedSelect.value = medId;
            sellMedSelect.dispatchEvent(new Event('change'));
        }

        function transferMedicineFromManufacturer(medId) {
            // In a real implementation, this would transfer from manufacturer to distributor
            alert(`This would initiate transfer of medicine ID ${medId} from manufacturer to distributor in a real blockchain system.`);
        }

        function purchaseMedicine(medId) {
            const medicine = state.medicines.find(m => m.id === medId);
            if (medicine) {
                alert(`This would initiate purchase of ${medicine.name} from the medical store in a real blockchain system.`);
            }
        }
    </script>
</body>
</html>
