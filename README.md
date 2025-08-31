<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستەمی بەکرێدانی سەیارە</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #3498db;
            --secondary-color: #2c3e50;
            --accent-color: #e74c3c;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --light-color: #ecf0f1;
            --dark-color: #34495e;
            --gradient-start: #3498db;
            --gradient-end: #2c3e50;
            --card-bg: #ffffff;
            --text-color: #333333;
            --border-radius: 12px;
            --box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%);
            color: var(--text-color);
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: rgba(255, 255, 255, 0.9);
            color: var(--secondary-color);
            padding: 1.5rem;
            text-align: center;
            border-radius: var(--border-radius);
            margin-bottom: 30px;
            box-shadow: var(--box-shadow);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }
        
        .logo {
            font-size: 2.5rem;
            color: var(--primary-color);
        }
        
        .tabs {
            display: flex;
            margin-bottom: 30px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
        }
        
        .tab {
            padding: 18px 25px;
            cursor: pointer;
            flex: 1;
            text-align: center;
            transition: all 0.3s ease;
            font-weight: 600;
            font-size: 1.1rem;
            color: var(--secondary-color);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .tab.active {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
        }
        
        .tab:hover:not(.active) {
            background-color: rgba(52, 152, 219, 0.1);
        }
        
        .tab-content {
            display: none;
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            margin-bottom: 30px;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .tab-content.active {
            display: block;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: var(--secondary-color);
        }
        
        input, select, button, textarea {
            width: 100%;
            padding: 14px;
            border: 2px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        input:focus, select:focus, textarea:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
        }
        
        button {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            border: none;
            cursor: pointer;
            font-weight: 600;
            padding: 16px;
            transition: all 0.3s ease;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .search-container {
            position: relative;
            margin-bottom: 25px;
        }
        
        .suggestions {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background-color: white;
            border: 2px solid var(--primary-color);
            border-top: none;
            border-radius: 0 0 var(--border-radius) var(--border-radius);
            z-index: 100;
            max-height: 250px;
            overflow-y: auto;
            display: none;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
        }
        
        .suggestion-item {
            padding: 12px 15px;
            cursor: pointer;
            border-bottom: 1px solid #eee;
            transition: background-color 0.2s;
        }
        
        .suggestion-item:hover {
            background-color: #f0f8ff;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 25px;
            background-color: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        
        th, td {
            padding: 16px 20px;
            text-align: right;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            font-weight: 600;
        }
        
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        
        tr:hover {
            background-color: #f0f8ff;
        }
        
        .action-btn {
            padding: 8px 14px;
            margin: 0 5px;
            width: auto;
            font-size: 14px;
            border-radius: 6px;
        }
        
        .delete-btn {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
        }
        
        .view-btn {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
        }
        
        .car-card {
            border: 2px solid #ddd;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            background-color: white;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
        }
        
        .car-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
        }
        
        .car-card h3 {
            color: var(--primary-color);
            margin-bottom: 15px;
            font-size: 1.4rem;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }
        
        .car-details {
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }
        
        .car-detail {
            flex: 1 0 50%;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        
        .car-detail i {
            margin-left: 10px;
            color: var(--primary-color);
            font-size: 1.2rem;
        }
        
        .filter-section {
            background: linear-gradient(135deg, #f0f8ff 0%, #e3f2fd 100%);
            padding: 20px;
            border-radius: var(--border-radius);
            margin-bottom: 25px;
            border: 2px solid #ddd;
        }
        
        .date-filters {
            display: flex;
            gap: 20px;
            margin-bottom: 15px;
        }
        
        .date-filters .form-group {
            flex: 1;
            margin-bottom: 0;
        }
        
        .history-item {
            border-right: 5px solid var(--primary-color);
            padding: 18px;
            margin-bottom: 15px;
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .history-item.returned {
            border-right-color: var(--success-color);
        }
        
        .history-details {
            flex: 1;
        }
        
        .history-actions {
            display: flex;
            gap: 10px;
        }
        
        .status-badge {
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-right: 10px;
        }
        
        .status-active {
            background-color: #ffeaa7;
            color: #d35400;
        }
        
        .status-returned {
            background-color: #d1f7c4;
            color: #27ae60;
        }
        
        .card {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: var(--box-shadow);
        }
        
        .card-title {
            color: var(--primary-color);
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #eee;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            padding: 25px;
            border-radius: var(--border-radius);
            text-align: center;
            box-shadow: var(--box-shadow);
        }
        
        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            margin: 15px 0;
        }
        
        .stat-label {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        @media (max-width: 768px) {
            .tabs {
                flex-direction: column;
            }
            
            .date-filters {
                flex-direction: column;
                gap: 15px;
            }
            
            .car-detail {
                flex: 1 0 100%;
            }
            
            .history-item {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .history-actions {
                margin-top: 15px;
                align-self: flex-end;
            }
            
            .stats-container {
                grid-template-columns: 1fr;
            }
        }
        
        .print-btn {
            background: linear-gradient(135deg, #95a5a6 0%, #7f8c8d 100%);
            margin-top: 20px;
        }
        
        .section-title {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--secondary-color);
            margin: 25px 0 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eee;
        }
        
        .section-title i {
            color: var(--primary-color);
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <i class="logo fas fa-car"></i>
            <h1>سیستەمی بەکرێدانی سەیارە</h1>
        </header>
        
        <div class="tabs">
            <div class="tab active" data-tab="rent">
                <i class="fas fa-hand-holding-usd"></i>
                بەکرێدانی سەیارە
            </div>
            <div class="tab" data-tab="garage">
                <i class="fas fa-warehouse"></i>
                گەراج
            </div>
            <div class="tab" data-tab="history">
                <i class="fas fa-history"></i>
                مێژووی بەکرێدان
            </div>
            <div class="tab" data-tab="stats">
                <i class="fas fa-chart-line"></i>
                ئامارەکان
            </div>
        </div>
        
        <!-- بەشی بەکرێدانی سەیارە -->
        <div class="tab-content active" id="rent-tab">
            <h2 class="section-title"><i class="fas fa-hand-holding-usd"></i> بەکرێدانی سەیارە</h2>
            
            <div class="search-container">
                <input type="text" id="car-search" placeholder="گەڕان بەدوای ناوی سەیارە...">
                <div class="suggestions" id="car-suggestions"></div>
            </div>
            
            <div id="selected-car" style="display: none;">
                <div class="car-card">
                    <h3 id="selected-car-name"></h3>
                    <div class="car-details">
                        <div class="car-detail"><i class="fas fa-palette"></i> <strong>رەنگ:</strong> <span id="selected-car-color"></span></div>
                        <div class="car-detail"><i class="fas fa-hashtag"></i> <strong>ژمارەی سەیارە:</strong> <span id="selected-car-number"></span></div>
                        <div class="car-detail"><i class="fas fa-car-side"></i> <strong>جۆری سەیارە:</strong> <span id="selected-car-type"></span></div>
                        <div class="car-detail"><i class="fas fa-tag"></i> <strong>نرخی بەکرێ:</strong> <span id="selected-car-price"></span> دینار/رۆژ</div>
                    </div>
                    <button id="add-to-cart" class="action-btn"><i class="fas fa-cart-plus"></i> زیادکردن بۆ سەبەت</button>
                </div>
            </div>
            
            <div class="form-group">
                <label for="customer-name"><i class="fas fa-user"></i> ناوی کەسی بەکرێدهێنەر:</label>
                <input type="text" id="customer-name" placeholder="ناوی کەس بنووسە...">
                <div class="suggestions" id="customer-suggestions"></div>
            </div>
            
            <div class="form-group">
                <label for="rent-date"><i class="fas fa-calendar-alt"></i> بەرواری بەکرێدان:</label>
                <input type="date" id="rent-date">
            </div>
            
            <div class="form-group">
                <label for="return-date"><i class="fas fa-calendar-check"></i> بەرواری وەرگرتنەوە:</label>
                <input type="date" id="return-date">
            </div>
            
            <div class="form-group">
                <label for="total-price"><i class="fas fa-money-bill-wave"></i> کۆی گشتی:</label>
                <input type="text" id="total-price" readonly>
            </div>
            
            <button id="confirm-rent"><i class="fas fa-check-circle"></i> دەسڵاتدان بە بەکرێدان</button>
        </div>
        
        <!-- بەشی گەراج -->
        <div class="tab-content" id="garage-tab">
            <h2 class="section-title"><i class="fas fa-warehouse"></i> بەشی گەراج</h2>
            
            <div class="card">
                <h3 class="card-title"><i class="fas fa-plus-circle"></i> زیادکردنی سەیارەی نوێ</h3>
                <form id="add-car-form">
                    <div class="form-group">
                        <label for="car-name">ناوی سەیارە:</label>
                        <input type="text" id="car-name" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="car-model">مۆدێلی سەیارە:</label>
                        <input type="text" id="car-model" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="car-color">رەنگی سەیارە:</label>
                        <input type="text" id="car-color" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="car-number">ژمارەی سەیارە:</label>
                        <input type="text" id="car-number" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="car-type">جۆری سەیارە:</label>
                        <select id="car-type" required>
                            <option value="">جۆری سەیارە هەڵبژێرە</option>
                            <option value="سدان">سدان</option>
                            <option value="هەتچباک">هەتچباک</option>
                            <option value="SUV">SUV</option>
                            <option value="پیکاپ">پیکاپ</option>
                            <option value="ڤان">ڤان</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="rent-price">نرخی بەکرێ (دینار/رۆژ):</label>
                        <input type="number" id="rent-price" min="0" required>
                    </div>
                    
                    <button type="submit"><i class="fas fa-save"></i> زیادکردنی سەیارە</button>
                </form>
            </div>
            
            <h3 class="section-title"><i class="fas fa-car"></i> لیستی سەیارەکان</h3>
            <div id="cars-list">
                <!-- لیستی سەیارەکان لێرە زیاد دەبێت -->
            </div>
        </div>
        
        <!-- بەشی مێژووی بەکرێدان -->
        <div class="tab-content" id="history-tab">
            <h2 class="section-title"><i class="fas fa-history"></i> مێژووی بەکرێدان</h2>
            
            <div class="filter-section">
                <h3><i class="fas fa-filter"></i> فلترکردن بەپێی بەروار</h3>
                <div class="date-filters">
                    <div class="form-group">
                        <label for="filter-start-date">لە بەروار:</label>
                        <input type="date" id="filter-start-date">
                    </div>
                    <div class="form-group">
                        <label for="filter-end-date">بۆ بەروار:</label>
                        <input type="date" id="filter-end-date">
                    </div>
                </div>
                <button id="apply-filter"><i class="fas fa-check"></i> جێبەجێکردنی فلتر</button>
                <button id="clear-filter" class="action-btn"><i class="fas fa-times"></i> سڕینەوەی فلتر</button>
            </div>
            
            <div id="rental-history-list">
                <!-- مێژووی بەکرێدان لێرە زیاد دەبێت -->
            </div>
            
            <button class="print-btn" id="print-history"><i class="fas fa-print"></i> چاپکردنی مێژوو</button>
        </div>
        
        <!-- بەشی ئامارەکان -->
        <div class="tab-content" id="stats-tab">
            <h2 class="section-title"><i class="fas fa-chart-line"></i> ئامارەکان</h2>
            
            <div class="stats-container">
                <div class="stat-card">
                    <i class="fas fa-car-side fa-3x"></i>
                    <div class="stat-number" id="total-cars">0</div>
                    <div class="stat-label">سەیارەی بەردەست</div>
                </div>
                
                <div class="stat-card">
                    <i class="fas fa-hand-holding-usd fa-3x"></i>
                    <div class="stat-number" id="active-rentals">0</div>
                    <div class="stat-label">بەکرێدانی چالاک</div>
                </div>
                
                <div class="stat-card">
                    <i class="fas fa-money-bill-wave fa-3x"></i>
                    <div class="stat-number" id="total-revenue">0 دینار</div>
                    <div class="stat-label">داهاتی گشتی</div>
                </div>
            </div>
            
            <div class="card">
                <h3 class="card-title"><i class="fas fa-chart-pie"></i> دابەشبوونی سەیارەکان بەپێی جۆر</h3>
                <div id="car-type-chart">
                    <!-- وێنەی دابەشبوونی جۆری سەیارەکان -->
                    <p style="text-align: center; padding: 20px;">هیچ داتایەک بەردەست نیە بۆ پیشاندان</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // داتا و فەنکشنە سەرەکییەکان
        const app = {
            cars: JSON.parse(localStorage.getItem('cars')) || [],
            customers: JSON.parse(localStorage.getItem('customers')) || [],
            rentals: JSON.parse(localStorage.getItem('rentals')) || [],
            currentTab: 'rent',
            
            init: function() {
                this.setupEventListeners();
                this.renderCarsList();
                this.renderRentalHistory();
                this.updateStats();
                this.generateSampleData();
            },
            
            setupEventListeners: function() {
                // گۆڕینی تابەکان
                document.querySelectorAll('.tab').forEach(tab => {
                    tab.addEventListener('click', () => {
                        document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                        document.querySelectorAll('.tab-content').forEach(tc => tc.classList.remove('active'));
                        
                        tab.classList.add('active');
                        document.getElementById(`${tab.dataset.tab}-tab`).classList.add('active');
                        this.currentTab = tab.dataset.tab;
                        
                        if (this.currentTab === 'stats') {
                            this.updateStats();
                        }
                    });
                });
                
                // گەڕان بەدوای سەیارە
                document.getElementById('car-search').addEventListener('input', (e) => {
                    this.showCarSuggestions(e.target.value);
                });
                
                // زیادکردنی سەیارە بۆ سەبەت
                document.getElementById('add-to-cart').addEventListener('click', () => {
                    this.addToCart();
                });
                
                // گەڕان بەدوای کەس
                document.getElementById('customer-name').addEventListener('input', (e) => {
                    this.showCustomerSuggestions(e.target.value);
                });
                
                // زیادکردنی سەیارە نوێ
                document.getElementById('add-car-form').addEventListener('submit', (e) => {
                    e.preventDefault();
                    this.addNewCar();
                });
                
                // دەسڵاتدان بە بەکرێدان
                document.getElementById('confirm-rent').addEventListener('click', () => {
                    this.confirmRental();
                });
                
                // ژماردنەوەی کۆی گشتی
                document.getElementById('return-date').addEventListener('change', () => {
                    this.calculateTotalPrice();
                });
                
                // جێبەجێکردنی فلتر
                document.getElementById('apply-filter').addEventListener('click', () => {
                    this.applyFilter();
                });
                
                // سڕینەوەی فلتر
                document.getElementById('clear-filter').addEventListener('click', () => {
                    document.getElementById('filter-start-date').value = '';
                    document.getElementById('filter-end-date').value = '';
                    this.renderRentalHistory();
                });
                
                // چاپکردنی مێژوو
                document.getElementById('print-history').addEventListener('click', () => {
                    window.print();
                });
            },
            
            generateSampleData: function() {
                if (this.cars.length === 0) {
                    const sampleCars = [
                        {id: 1, name: "تۆیۆتا", model: "کامری", color: "سپی", number: "12345", type: "سدان", rentPrice: 50000, available: true},
                        {id: 2, name: "هیوندا", model: "ئێلانترا", color: "ڕەش", number: "67890", type: "سدان", rentPrice: 45000, available: true},
                        {id: 3, name: "کیا", model: "سۆرێنتۆ", color: "شین", number: "54321", type: "SUV", rentPrice: 70000, available: true}
                    ];
                    
                    this.cars = sampleCars;
                    this.saveToLocalStorage('cars', this.cars);
                }
                
                if (this.customers.length === 0) {
                    const sampleCustomers = ["ئەحمەد محەممەد", "سارا عەبدوڵڵا", "عەلی مستەفا"];
                    this.customers = sampleCustomers;
                    this.saveToLocalStorage('customers', this.customers);
                }
                
                if (this.rentals.length === 0) {
                    const sampleRentals = [
                        {id: 1, customerName: "ئەحمەد محەممەد", carId: 1, carName: "تۆیۆتا کامری", rentDate: "2023-10-01", returnDate: "2023-10-05", totalPrice: "200000 دینار (بۆ 4 رۆژ)", status: "returned"},
                        {id: 2, customerName: "سارا عەبدوڵڵا", carId: 3, carName: "کیا سۆرێنتۆ", rentDate: "2023-10-10", returnDate: "2023-10-15", totalPrice: "350000 دینار (بۆ 5 رۆژ)", status: "returned"}
                    ];
                    
                    this.rentals = sampleRentals;
                    this.saveToLocalStorage('rentals', this.rentals);
                }
                
                this.renderCarsList();
                this.renderRentalHistory();
            },
            
            showCarSuggestions: function(query) {
                const suggestionsContainer = document.getElementById('car-suggestions');
                suggestionsContainer.innerHTML = '';
                
                if (query.length < 2) {
                    suggestionsContainer.style.display = 'none';
                    return;
                }
                
                const filteredCars = this.cars.filter(car => 
                    car.name.toLowerCase().includes(query.toLowerCase()) ||
                    car.model.toLowerCase().includes(query.toLowerCase())
                );
                
                if (filteredCars.length > 0) {
                    filteredCars.forEach(car => {
                        const div = document.createElement('div');
                        div.className = 'suggestion-item';
                        div.innerHTML = `<i class="fas fa-car"></i> ${car.name} ${car.model} - ${car.number}`;
                        div.addEventListener('click', () => {
                            this.selectCar(car);
                            suggestionsContainer.style.display = 'none';
                        });
                        suggestionsContainer.appendChild(div);
                    });
                    suggestionsContainer.style.display = 'block';
                } else {
                    suggestionsContainer.style.display = 'none';
                }
            },
            
            selectCar: function(car) {
                document.getElementById('selected-car').style.display = 'block';
                document.getElementById('selected-car-name').textContent = `${car.name} ${car.model}`;
                document.getElementById('selected-car-color').textContent = car.color;
                document.getElementById('selected-car-number').textContent = car.number;
                document.getElementById('selected-car-type').textContent = car.type;
                document.getElementById('selected-car-price').textContent = car.rentPrice.toLocaleString();
                
                // هەڵگرتنی ئایدی سەیارە بۆ بەکارهێنانی دواتر
                document.getElementById('selected-car').dataset.carId = car.id;
                
                this.calculateTotalPrice();
            },
            
            calculateTotalPrice: function() {
                const rentDate = new Date(document.getElementById('rent-date').value);
                const returnDate = new Date(document.getElementById('return-date').value);
                
                if (rentDate && returnDate && returnDate > rentDate) {
                    const days = Math.ceil((returnDate - rentDate) / (1000 * 60 * 60 * 24));
                    const carId = document.getElementById('selected-car').dataset.carId;
                    
                    if (carId) {
                        const car = this.cars.find(c => c.id == carId);
                        if (car) {
                            const totalPrice = days * car.rentPrice;
                            document.getElementById('total-price').value = `${totalPrice.toLocaleString()} دینار (بۆ ${days} رۆژ)`;
                            return;
                        }
                    }
                }
                
                document.getElementById('total-price').value = '';
            },
            
            addToCart: function() {
                // لەم نموونەدا، ئێمە ڕاستەوخۆ بەکرێدەدرێت
                // لە سیستەمێکی ڕاستەقینەدا، ئەمە زیاد دەکرێت بۆ سەبەت
                alert('سەیارە زیادکرا بۆ سەبەت!');
            },
            
            showCustomerSuggestions: function(query) {
                const suggestionsContainer = document.getElementById('customer-suggestions');
                suggestionsContainer.innerHTML = '';
                
                if (query.length < 2) {
                    suggestionsContainer.style.display = 'none';
                    return;
                }
                
                const filteredCustomers = this.customers.filter(customer => 
                    customer.toLowerCase().includes(query.toLowerCase())
                );
                
                if (filteredCustomers.length > 0) {
                    filteredCustomers.forEach(customer => {
                        const div = document.createElement('div');
                        div.className = 'suggestion-item';
                        div.innerHTML = `<i class="fas fa-user"></i> ${customer}`;
                        div.addEventListener('click', () => {
                            document.getElementById('customer-name').value = customer;
                            suggestionsContainer.style.display = 'none';
                        });
                        suggestionsContainer.appendChild(div);
                    });
                    suggestionsContainer.style.display = 'block';
                } else {
                    suggestionsContainer.style.display = 'none';
                }
            },
            
            addNewCar: function() {
                const name = document.getElementById('car-name').value;
                const model = document.getElementById('car-model').value;
                const color = document.getElementById('car-color').value;
                const number = document.getElementById('car-number').value;
                const type = document.getElementById('car-type').value;
                const rentPrice = parseInt(document.getElementById('rent-price').value);
                
                const newCar = {
                    id: Date.now(), // ناسکەرەوەی تاک
                    name,
                    model,
                    color,
                    number,
                    type,
                    rentPrice,
                    available: true
                };
                
                this.cars.push(newCar);
                this.saveToLocalStorage('cars', this.cars);
                this.renderCarsList();
                
                // پاککردنەوەی فۆرم
                document.getElementById('add-car-form').reset();
                
                alert('سەیارە بە سەرکەوتوویی زیادکرا!');
            },
            
            confirmRental: function() {
                const customerName = document.getElementById('customer-name').value;
                const rentDate = document.getElementById('rent-date').value;
                const returnDate = document.getElementById('return-date').value;
                const carId = document.getElementById('selected-car').dataset.carId;
                
                if (!customerName || !rentDate || !returnDate || !carId) {
                    alert('تکایە هەموو خانەکان پڕبکەرەوە!');
                    return;
                }
                
                const car = this.cars.find(c => c.id == carId);
                if (!car) {
                    alert('هەڵە! سەیارە نەدۆزرایەوە.');
                    return;
                }
                
                // زیادکردنی کڕیارە نوێیەکە بۆ لیستەکە ئەگەر بوونی نییە
                if (!this.customers.includes(customerName)) {
                    this.customers.push(customerName);
                    this.saveToLocalStorage('customers', this.customers);
                }
                
                // دروستکردنی تۆمارێکی بەکرێدان
                const rental = {
                    id: Date.now(),
                    customerName,
                    carId,
                    carName: `${car.name} ${car.model}`,
                    rentDate,
                    returnDate,
                    totalPrice: document.getElementById('total-price').value,
                    status: 'active'
                };
                
                this.rentals.push(rental);
                this.saveToLocalStorage('rentals', this.rentals);
                
                // نەخشێنانی مێژووی بەکرێدان
                this.renderRentalHistory();
                
                // پاککردنەوەی فۆرم
                document.getElementById('customer-name').value = '';
                document.getElementById('rent-date').value = '';
                document.getElementById('return-date').value = '';
                document.getElementById('total-price').value = '';
                document.getElementById('selected-car').style.display = 'none';
                
                alert('بەکرێدانەکە تۆمارکرا!');
            },
            
            renderCarsList: function() {
                const carsList = document.getElementById('cars-list');
                carsList.innerHTML = '';
                
                if (this.cars.length === 0) {
                    carsList.innerHTML = '<p>هیچ سەیارەیەک تۆمارنەکراوە.</p>';
                    return;
                }
                
                this.cars.forEach(car => {
                    const carCard = document.createElement('div');
                    carCard.className = 'car-card';
                    carCard.innerHTML = `
                        <h3>${car.name} ${car.model}</h3>
                        <div class="car-details">
                            <div class="car-detail"><i class="fas fa-palette"></i> <strong>رەنگ:</strong> ${car.color}</div>
                            <div class="car-detail"><i class="fas fa-hashtag"></i> <strong>ژمارەی سەیارە:</strong> ${car.number}</div>
                            <div class="car-detail"><i class="fas fa-car-side"></i> <strong>جۆری سەیارە:</strong> ${car.type}</div>
                            <div class="car-detail"><i class="fas fa-tag"></i> <strong>نرخی بەکرێ:</strong> ${car.rentPrice.toLocaleString()} دینار/رۆژ</div>
                            <div class="car-detail"><i class="fas fa-check-circle"></i> <strong>بەردەستە:</strong> ${car.available ? 'بەڵێ' : 'نەخێر'}</div>
                        </div>
                        <button class="action-btn delete-btn" data-car-id="${car.id}"><i class="fas fa-trash"></i> سڕینەوە</button>
                    `;
                    
                    carsList.appendChild(carCard);
                });
                
                // زیادکردنی فەرمانی سڕینەوە
                document.querySelectorAll('.delete-btn').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const carId = e.target.closest('button').dataset.carId;
                        this.deleteCar(carId);
                    });
                });
            },
            
            renderRentalHistory: function() {
                const historyContainer = document.getElementById('rental-history-list');
                historyContainer.innerHTML = '';
                
                if (this.rentals.length === 0) {
                    historyContainer.innerHTML = '<p style="text-align: center; padding: 20px;">هیچ مێژویێکی بەکرێدان نیە.</p>';
                    return;
                }
                
                // فلترکردنی بەپێی بەروار ئەگەر دیاریکرابێت
                let filteredRentals = this.rentals;
                const startDate = document.getElementById('filter-start-date').value;
                const endDate = document.getElementById('filter-end-date').value;
                
                if (startDate) {
                    filteredRentals = filteredRentals.filter(rental => rental.rentDate >= startDate);
                }
                
                if (endDate) {
                    filteredRentals = filteredRentals.filter(rental => rental.rentDate <= endDate);
                }
                
                filteredRentals.forEach(rental => {
                    const historyItem = document.createElement('div');
                    historyItem.className = `history-item ${rental.status === 'returned' ? 'returned' : ''}`;
                    
                    historyItem.innerHTML = `
                        <div class="history-details">
                            <h4>${rental.customerName} - ${rental.carName}</h4>
                            <p><strong>بەرواری بەکرێدان:</strong> ${rental.rentDate}</p>
                            <p><strong>بەرواری وەرگرتنەوە:</strong> ${rental.returnDate}</p>
                            <p><strong>کۆی گشتی:</strong> ${rental.totalPrice}</p>
                            <span class="status-badge ${rental.status === 'active' ? 'status-active' : 'status-returned'}">
                                ${rental.status === 'active' ? 'چالاک' : 'گەڕێندراوەتەوە'}
                            </span>
                        </div>
                        <div class="history-actions">
                            <button class="action-btn view-btn" data-rental-id="${rental.id}"><i class="fas fa-eye"></i></button>
                            <button class="action-btn delete-btn" data-rental-id="${rental.id}"><i class="fas fa-trash"></i></button>
                        </div>
                    `;
                    
                    historyContainer.appendChild(historyItem);
                });
                
                // زیادکردنی فەرمانی سڕینەوە بۆ مێژووی بەکرێدان
                document.querySelectorAll('#rental-history-list .delete-btn').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const rentalId = e.target.closest('button').dataset.rentalId;
                        this.deleteRental(rentalId);
                    });
                });
            },
            
            applyFilter: function() {
                this.renderRentalHistory();
            },
            
            updateStats: function() {
                // ژماردنی سەیارە بەردەستەکان
                document.getElementById('total-cars').textContent = this.cars.length;
                
                // ژماردنی بەکرێدانی چالاک
                const activeRentals = this.rentals.filter(rental => rental.status === 'active').length;
                document.getElementById('active-rentals').textContent = activeRentals;
                
                // ژماردنی داهاتی گشتی
                const totalRevenue = this.rentals.reduce((total, rental) => {
                    if (rental.status === 'returned') {
                        const price = parseInt(rental.totalPrice.replace(/\D/g, ''));
                        return total + (price || 0);
                    }
                    return total;
                }, 0);
                
                document.getElementById('total-revenue').textContent = `${totalRevenue.toLocaleString()} دینار`;
            },
            
            deleteCar: function(carId) {
                if (confirm('دڵنیایت لە سڕینەوەی ئەم سەیارەیە؟')) {
                    this.cars = this.cars.filter(car => car.id != carId);
                    this.saveToLocalStorage('cars', this.cars);
                    this.renderCarsList();
                    alert('سەیارە سڕدرایەوە!');
                }
            },
            
            deleteRental: function(rentalId) {
                if (confirm('دڵنیایت لە سڕینەوەی ئەم تۆمارە؟')) {
                    this.rentals = this.rentals.filter(rental => rental.id != rentalId);
                    this.saveToLocalStorage('rentals', this.rentals);
                    this.renderRentalHistory();
                    alert('تۆمارەکە سڕدرایەوە!');
                }
            },
            
            saveToLocalStorage: function(key, data) {
                localStorage.setItem(key, JSON.stringify(data));
            }
        };
        
        // دەستپێکردنی ئەپەکە
        document.addEventListener('DOMContentLoaded', function() {
            app.init();
        });
    </script>
</body>
</html>
