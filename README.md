<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستەمی داخیل کردنی ناو و وێنە</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            color: #333;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .container {
            width: 100%;
            max-width: 800px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(90deg, #4776E6 0%, #8E54E9 100%);
            color: white;
            padding: 25px;
            text-align: center;
        }
        
        h1 {
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        .description {
            font-size: 16px;
            opacity: 0.9;
        }
        
        .form-section {
            padding: 30px;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #444;
        }
        
        input[type="text"],
        input[type="file"] {
            width: 100%;
            padding: 14px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        input[type="text"]:focus {
            border-color: #4776E6;
            outline: none;
        }
        
        .color-picker {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .color-option {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            transition: transform 0.2s;
            border: 3px solid white;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .color-option:hover {
            transform: scale(1.1);
        }
        
        .color-option.selected {
            border: 3px solid #333;
            transform: scale(1.1);
        }
        
        .btn {
            background: linear-gradient(90deg, #4776E6 0%, #8E54E9 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            border-radius: 8px;
            cursor: pointer;
            width: 100%;
            font-weight: 600;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .preview-section {
            padding: 30px;
            border-top: 1px solid #eee;
            text-align: center;
        }
        
        .preview-title {
            margin-bottom: 20px;
            color: #444;
        }
        
        .preview-content {
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: background-color 0.3s;
        }
        
        .preview-image {
            max-width: 200px;
            max-height: 200px;
            border-radius: 10px;
            margin-bottom: 15px;
            display: none;
        }
        
        .preview-name {
            font-size: 24px;
            font-weight: bold;
        }
        
        footer {
            background-color: #f5f5f5;
            text-align: center;
            padding: 20px;
            color: #666;
            font-size: 14px;
        }
        
        @media (max-width: 600px) {
            .container {
                border-radius: 10px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .form-section, .preview-section {
                padding: 20px;
            }
            
            .color-option {
                width: 40px;
                height: 40px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>سیستەمی داخیل کردنی ناو و وێنە</h1>
            <p class="description">ناو و وێنە خۆت داخیل بکە و رەنگێک هەڵبژێرە</p>
        </header>
        
        <div class="form-section">
            <div class="form-group">
                <label for="name">ناو</label>
                <input type="text" id="name" placeholder="ناوەکەت ئێرە بنووسە...">
            </div>
            
            <div class="form-group">
                <label for="image">وێنە</label>
                <input type="file" id="image" accept="image/*">
            </div>
            
            <div class="form-group">
                <label>رەنگ هەڵبژێرە</label>
                <div class="color-picker">
                    <div class="color-option selected" style="background-color: #6a11cb;" data-color="#6a11cb"></div>
                    <div class="color-option" style="background-color: #2575fc;" data-color="#2575fc"></div>
                    <div class="color-option" style="background-color: #ff416c;" data-color="#ff416c"></div>
                    <div class="color-option" style="background-color: #ff4b2b;" data-color="#ff4b2b"></div>
                    <div class="color-option" style="background-color: #7b4397;" data-color="#7b4397"></div>
                    <div class="color-option" style="background-color: #11998e;" data-color="#11998e"></div>
                    <div class="color-option" style="background-color: #38ef7d;" data-color="#38ef7d"></div>
                    <div class="color-option" style="background-color: #f5af19;" data-color="#f5af19"></div>
                </div>
            </div>
            
            <button class="btn" id="submitBtn">نیشانی پێشبینیکراو</button>
        </div>
        
        <div class="preview-section">
            <h2 class="preview-title">پێشبینیکراو</h2>
            <div class="preview-content" id="previewContent" style="background-color: #f9f9f9;">
                <img class="preview-image" id="previewImage">
                <div class="preview-name" id="previewName">ناو و وێنەکەت لێرە دەردەکەوێت</div>
            </div>
        </div>
        
        <footer>
            <p>ئەم سیستەمە لەلایەن تۆوە هۆست کراوە لە Vercel 🚀</p>
        </footer>
    </div>

    <script>
        // هەڵبژاردنی رەنگ
        const colorOptions = document.querySelectorAll('.color-option');
        const previewContent = document.getElementById('previewContent');
        
        colorOptions.forEach(option => {
            option.addEventListener('click', () => {
                // لابردنی هەموو هەڵبژاردنەکان
                colorOptions.forEach(opt => opt.classList.remove('selected'));
                
                // دانانی هەڵبژاردنی نوێ
                option.classList.add('selected');
                
                // گۆرینی رەنگی پێشبینیکراو
                const selectedColor = option.getAttribute('data-color');
                previewContent.style.backgroundColor = selectedColor;
            });
        });
        
        // پێشبینیکردنی وێنە
        const imageInput = document.getElementById('image');
        const previewImage = document.getElementById('previewImage');
        
        imageInput.addEventListener('change', function() {
            const file = this.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    previewImage.src = e.target.result;
                    previewImage.style.display = 'block';
                }
                reader.readAsDataURL(file);
            }
        });
        
        // نیشاندانی پێشبینیکراو
        const submitBtn = document.getElementById('submitBtn');
        const nameInput = document.getElementById('name');
        const previewName = document.getElementById('previewName');
        
        submitBtn.addEventListener('click', function() {
            if (nameInput.value.trim() !== '') {
                previewName.textContent = nameInput.value;
            } else {
                previewName.textContent = "ناوەکەت داخیل بکە!";
            }
            
            // هەڵبژاردنی رەنگی هەڵبژێردراو
            const selectedColorOption = document.querySelector('.color-option.selected');
            const selectedColor = selectedColorOption.getAttribute('data-color');
            previewContent.style.backgroundColor = selectedColor;
        });
    </script>
</body>
</html>
