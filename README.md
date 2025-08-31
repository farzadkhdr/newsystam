<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستەمی بە کرێدانی سەیارە</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.3/font/bootstrap-icons.css">
    <style>
        body {
            background-color: #f8f9fa;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        .sidebar {
            background-color: #343a40;
            color: white;
            height: 100vh;
            position: fixed;
            padding-top: 20px;
        }
        .sidebar a {
            color: white;
            text-decoration: none;
            display: block;
            padding: 15px;
            margin: 5px 0;
            border-radius: 5px;
        }
        .sidebar a:hover, .sidebar a.active {
            background-color: #495057;
        }
        .main-content {
            margin-right: 250px;
            padding: 20px;
        }
        .section {
            display: none;
        }
        .section.active {
            display: block;
        }
        .card {
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            border: none;
            border-radius: 10px;
        }
        .card-header {
            background-color: #0d6efd;
            color: white;
            border-radius: 10px 10px 0 0 !important;
        }
        .table-hover tbody tr:hover {
            background-color: rgba(13, 110, 253, 0.1);
        }
        .search-box {
            position: relative;
        }
        .suggestions {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: white;
            border: 1px solid #ddd;
            border-radius: 0 0 5px 5px;
            z-index: 1000;
            display: none;
        }
        .suggestion-item {
            padding: 10px;
            cursor: pointer;
        }
        .suggestion-item:hover {
            background-color: #f0f0f0;
        }
        .car-image {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="sidebar" style="width: 250px;">
        <h4 class="text-center mb-4">سیستەمی بە کرێدانی سەیارە</h4>
        <a href="#" class="active" data-section="rent-car"><i class="bi bi-car-front"></i> بە کرێدانی سەیارە</a>
        <a href="#" data-section="rental-history"><i class="bi bi-clock-history"></i> مێژووی بە کرێدان</a>
        <a href="#" data-section="garage"><i class="bi bi-house-gear"></i> گەراج و سەیارە</a>
    </div>

    <div class="main-content">
        <!-- بەشی بە کرێدانی سەیارە -->
        <div id="rent-car" class="section active">
            <h2 class="mb-4">بە کرێدانی سەیارە</h2>
            
            <div class="card mb-4">
                <div class="card-header">
                    <h5 class="mb-0">گەڕان بەدوای سەیارە</h5>
                </div>
                <div class="card-body">
                    <div class="row mb-3">
                        <div class="col-md-6">
                            <div class="search-box">
                                <input type="text" class="form-control" id="car-search" placeholder="ناوی سەیارە بنووسە...">
                                <div class="suggestions" id="car-suggestions"></div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="row" id="car-results">
                        <!-- نەخشەکانی سەیارەکان لێرە دەردەکەون -->
                    </div>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h5 class="mb-0">کەسی بەکرێدهێنەر</h5>
                </div>
                <div class="card-body">
                    <form id="renter-form">
                        <div class="row mb-3">
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="renter-name" placeholder="ناوی کەسەکە">
                            </div>
                            <div class="col-md-4">
                                <input type="tel" class="form-control" id="renter-phone" placeholder="ژمارەی موبایل">
                            </div>
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="renter-address" placeholder="ناونیشان">
                            </div>
                        </div>
                        <div class="row mb-3">
                            <div class="col-md-6">
                                <input type="file" class="form-control" id="id-card" accept="image/*">
                                <small class="form-text text-muted">وێنەی کارتی نیشتمانی</small>
                            </div>
                            <div class="col-md-6">
                                <div class="search-box">
                                    <input type="text" class="form-control" id="customer-search" placeholder="گەڕان بەدوای کەسەکان...">
                                    <div class="suggestions" id="customer-suggestions"></div>
                                </div>
                            </div>
                        </div>
                        <div class="row mb-3">
                            <div class="col-md-4">
                                <label for="rent-date" class="form-label">بەرواری بەکرێدان</label>
                                <input type="date" class="form-control" id="rent-date">
                            </div>
                            <div class="col-md-4">
                                <label for="return-date" class="form-label">بەرواری وەرگرتنەوە</label>
                                <input type="date" class="form-control" id="return-date">
                            </div>
                            <div class="col-md-4">
                                <label for="rent-price" class="form-label">بڕی پارەی بەکرێدان</label>
                                <input type="number" class="form-control" id="rent-price" placeholder="بڕی پارە">
                            </div>
                        </div>
                        <button type="submit" class="btn btn-primary">تۆمارکردنی بەکرێدان</button>
                    </form>
                </div>
            </div>
        </div>

        <!-- بەشی مێژووی بە کرێدان -->
        <div id="rental-history" class="section">
            <h2 class="mb-4">مێژووی بە کرێدان</h2>
            
            <div class="card mb-4">
                <div class="card-header">
                    <h5 class="mb-0">فلترکردن</h5>
                </div>
                <div class="card-body">
                    <div class="row mb-3">
                        <div class="col-md-4">
                            <label for="filter-start-date" class="form-label">بەرواری دەستپێک</label>
                            <input type="date" class="form-control" id="filter-start-date">
                        </div>
                        <div class="col-md-4">
                            <label for="filter-end-date" class="form-label">بەرواری کۆتایی</label>
                            <input type="date" class="form-control" id="filter-end-date">
                        </div>
                        <div class="col-md-4">
                            <label for="filter-customer" class="form-label">کەس</label>
                            <input type="text" class="form-control" id="filter-customer" placeholder="ناوی کەس">
                        </div>
                    </div>
                    <button class="btn btn-primary" id="apply-filter">جێبەجێکردنی فلتر</button>
                    <button class="btn btn-secondary" id="print-history">چاپکردن</button>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h5 class="mb-0">مێژووی بە کرێدان</h5>
                </div>
                <div class="card-body">
                    <div class="table-responsive">
                        <table class="table table-striped table-hover">
                            <thead>
                                <tr>
                                    <th>ناوی کەس</th>
                                    <th>سەیارە</th>
                                    <th>بەرواری بەکرێدان</th>
                                    <th>بەرواری وەرگرتنەوە</th>
                                    <th>بڕی پارە</th>
                                    <th>کردار</th>
                                </tr>
                            </thead>
                            <tbody id="rental-history-table">
                                <!-- مێژووی بەکرێدان لێرە دەردەکەون -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- بەشی گەراج و سەیارە -->
        <div id="garage" class="section">
            <h2 class="mb-4">گەراج و سەیارە</h2>
            
            <div class="card mb-4">
                <div class="card-header">
                    <h5 class="mb-0">زیادکردنی سەیارەی نوێ</h5>
                </div>
                <div class="card-body">
                    <form id="car-form">
                        <div class="row mb-3">
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="car-name" placeholder="ناوی سەیارە" required>
                            </div>
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="car-model" placeholder="مۆدێلی سەیارە" required>
                            </div>
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="car-color" placeholder="رەنگی سەیارە" required>
                            </div>
                        </div>
                        <div class="row mb-3">
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="car-plate" placeholder="رەقەمی سەیارە" required>
                            </div>
                            <div class="col-md-4">
                                <input type="text" class="form-control" id="car-type" placeholder="جۆری سەیارە" required>
                            </div>
                            <div class="col-md-4">
                                <input type="file" class="form-control" id="car-image" accept="image/*">
                                <small class="form-text text-muted">وێنەی سەیارە</small>
                            </div>
                        </div>
                        <button type="submit" class="btn btn-primary">زیادکردنی سەیارە</button>
                    </form>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h5 class="mb-0">سەیارەکان</h5>
                </div>
                <div class="card-body">
                    <div class="row" id="car-list">
                        <!-- لیستی سەیارەکان لێرە دەردەکەون -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // نموونە داتا
        const sampleCars = [
            { id: 1, name: "تۆیۆتا کەمری", model: "2022", color: "سپی", plate: "12345ABC", type: "سدان", image: "https://via.placeholder.com/300x150?text=Toyota+Camry" },
            { id: 2, name: "هیوندا ئێلانترا", model: "2021", color: "ڕەش", plate: "67890XYZ", type: "سدان", image: "https://via.placeholder.com/300x150?text=Hyundai+Elantra" },
            { id: 3, name: "هۆندا سیڤیک", model: "2020", color: "شین", plate: "54321DEF", type: "سدان", image: "https://via.placeholder.com/300x150?text=Honda+Civic" }
        ];

        const sampleCustomers = [
            { id: 1, name: "عەلی محەممەد", phone: "07501234567", address: "هەولێر، کەوی ١٠" },
            { id: 2, name: "سارا عەبدوڵڵا", phone: "07507654321", address: "سلێمانی، شەقامی نەوشەوان" },
            { id: 3, name: "ئەحمەد حسن", phone: "07509876543", address: "دهۆک، ناوچەی ناوەندی" }
        ];

        let rentals = [];

        // گۆڕینی نێوان بەشەکان
        document.querySelectorAll('.sidebar a').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                // چالاککردنی لینکەکە
                document.querySelectorAll('.sidebar a').forEach(a => a.classList.remove('active'));
                this.classList.add('active');
                
                // نیشاندانی بەشی هەڵبژێردراو
                const sectionId = this.getAttribute('data-section');
                document.querySelectorAll('.section').forEach(section => section.classList.remove('active'));
                document.getElementById(sectionId).classList.add('active');
            });
        });

        // پێشنیاری ناوی سەیارە
        const carSearch = document.getElementById('car-search');
        const carSuggestions = document.getElementById('car-suggestions');

        carSearch.addEventListener('input', function() {
            const value = this.value.toLowerCase();
            carSuggestions.innerHTML = '';
            
            if (value) {
                const filteredCars = sampleCars.filter(car => 
                    car.name.toLowerCase().includes(value) || 
                    car.model.toLowerCase().includes(value)
                );
                
                if (filteredCars.length > 0) {
                    carSuggestions.style.display = 'block';
                    filteredCars.forEach(car => {
                        const div = document.createElement('div');
                        div.className = 'suggestion-item';
                        div.textContent = `${car.name} - ${car.model}`;
                        div.addEventListener('click', function() {
                            carSearch.value = car.name;
                            carSuggestions.style.display = 'none';
                            displayCarResults([car]);
                        });
                        carSuggestions.appendChild(div);
                    });
                } else {
                    carSuggestions.style.display = 'none';
                }
            } else {
                carSuggestions.style.display = 'none';
                displayCarResults(sampleCars);
            }
        });

        // پێشنیاری کەسی بەکرێدهێنەر
        const customerSearch = document.getElementById('customer-search');
        const customerSuggestions = document.getElementById('customer-suggestions');

        customerSearch.addEventListener('input', function() {
            const value = this.value.toLowerCase();
            customerSuggestions.innerHTML = '';
            
            if (value) {
                const filteredCustomers = sampleCustomers.filter(customer => 
                    customer.name.toLowerCase().includes(value)
                );
                
                if (filteredCustomers.length > 0) {
                    customerSuggestions.style.display = 'block';
                    filteredCustomers.forEach(customer => {
                        const div = document.createElement('div');
                        div.className = 'suggestion-item';
                        div.textContent = customer.name;
                        div.addEventListener('click', function() {
                            customerSearch.value = customer.name;
                            document.getElementById('renter-name').value = customer.name;
                            document.getElementById('renter-phone').value = customer.phone;
                            document.getElementById('renter-address').value = customer.address;
                            customerSuggestions.style.display = 'none';
                        });
                        customerSuggestions.appendChild(div);
                    });
                } else {
                    customerSuggestions.style.display = 'none';
                }
            } else {
                customerSuggestions.style.display = 'none';
            }
        });

        // نیشاندانی ئەنجامەکانی سەیارە
        function displayCarResults(cars) {
            const resultsContainer = document.getElementById('car-results');
            resultsContainer.innerHTML = '';
            
            cars.forEach(car => {
                const col = document.createElement('div');
                col.className = 'col-md-4 mb-3';
                col.innerHTML = `
                    <div class="card">
                        <img src="${car.image}" class="car-image" alt="${car.name}">
                        <div class="card-body">
                            <h5 class="card-title">${car.name}</h5>
                            <p class="card-text">
                                مۆدێل: ${car.model}<br>
                                رەنگ: ${car.color}<br>
                                رەقەم: ${car.plate}<br>
                                جۆر: ${car.type}
                            </p>
                            <button class="btn btn-primary btn-sm select-car" data-car-id="${car.id}">هەڵبژاردنی سەیارە</button>
                        </div>
                    </div>
                `;
                resultsContainer.appendChild(col);
            });
            
            // زیادکردنی ڕیەکسان بۆ هەڵبژاردنی سەیارە
            document.querySelectorAll('.select-car').forEach(button => {
                button.addEventListener('click', function() {
                    const carId = parseInt(this.getAttribute('data-car-id'));
                    const selectedCar = sampleCars.find(car => car.id === carId);
                    alert(`سەیارەی ${selectedCar.name} هەڵبژێردرا`);
                });
            });
        }

        // زیادکردنی کەسی نوێ
        document.getElementById('renter-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('renter-name').value;
            const phone = document.getElementById('renter-phone').value;
            const address = document.getElementById('renter-address').value;
            const rentDate = document.getElementById('rent-date').value;
            const returnDate = document.getElementById('return-date').value;
            const price = document.getElementById('rent-price').value;
            
            if (name && phone && rentDate && returnDate && price) {
                // لە ڕیالیەتدا، ئەم داتایە دەخرێتە ناو داتابەیسێکەوە
                alert("بەکرێدان تۆمارکرا!");
                this.reset();
            } else {
                alert("تکایە هەموو خانە پێویستەکان پڕبکەرەوە");
            }
        });

        // زیادکردنی سەیارەی نوێ
        document.getElementById('car-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('car-name').value;
            const model = document.getElementById('car-model').value;
            const color = document.getElementById('car-color').value;
            const plate = document.getElementById('car-plate').value;
            const type = document.getElementById('car-type').value;
            
            if (name && model && color && plate && type) {
                // لە ڕیالیەتدا، ئەم داتایە دەخرێتە ناو داتابەیسێکەوە
                alert("سەیارە زیادکرا!");
                this.reset();
            } else {
                alert("تکایە هەموو خانە پێویستەکان پڕبکەرەوە");
            }
        });

        // فلترکردنی مێژووی بەکرێدان
        document.getElementById('apply-filter').addEventListener('click', function() {
            // لە ڕیالیەتدا، ئەمە داتاکان لە داتابەیسەکە وەردەگرێت و فلتر دەکات
            alert("فلتر جێبەجێکرا!");
        });

        // چاپکردنی مێژووی بەکرێدان
        document.getElementById('print-history').addEventListener('click', function() {
            window.print();
        });

        // دەستپێکردنی سیستەمەکە
        document.addEventListener('DOMContentLoaded', function() {
            displayCarResults(sampleCars);
        });
    </script>
</body>
</html>
