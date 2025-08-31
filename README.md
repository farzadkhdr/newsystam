<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>چارەسەری کێشەی Failed to locate 'package.json'</title>
    <style>
        :root {
            --primary-color: #3498db;
            --secondary-color: #2c3e50;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --error-color: #e74c3c;
            --light-bg: #f8f9fa;
            --dark-text: #333;
            --light-text: #666;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            color: var(--dark-text);
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            padding: 2rem;
            text-align: center;
        }
        
        header h1 {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
        }
        
        header p {
            opacity: 0.9;
        }
        
        .content {
            padding: 2rem;
        }
        
        .error-section {
            background-color: #fff4f4;
            border-left: 5px solid var(--error-color);
            padding: 1.5rem;
            margin-bottom: 2rem;
            border-radius: 4px;
        }
        
        .error-title {
            color: var(--error-color);
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 1rem;
        }
        
        .solution-section {
            margin-bottom: 2.5rem;
        }
        
        .solution-title {
            color: var(--secondary-color);
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 1rem;
        }
        
        .steps {
            list-style-type: none;
            counter-reset: step-counter;
        }
        
        .steps li {
            margin-bottom: 1.5rem;
            padding-right: 3rem;
            position: relative;
            line-height: 1.6;
        }
        
        .steps li:before {
            counter-increment: step-counter;
            content: counter(step-counter);
            position: absolute;
            right: 0;
            top: 0;
            width: 2rem;
            height: 2rem;
            background-color: var(--primary-color);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        
        .code-block {
            background-color: #2d2d2d;
            color: #f8f8f2;
            padding: 1.2rem;
            border-radius: 6px;
            overflow-x: auto;
            margin: 1.2rem 0;
            font-family: 'Courier New', monospace;
            direction: ltr;
            text-align: left;
        }
        
        .file-structure {
            background-color: var(--light-bg);
            padding: 1.5rem;
            border-radius: 6px;
            margin: 1.2rem 0;
            font-family: 'Courier New', monospace;
        }
        
        .note {
            background-color: #f0f8ff;
            border-left: 5px solid var(--primary-color);
            padding: 1.2rem;
            margin: 1.2rem 0;
            border-radius: 4px;
        }
        
        .success-message {
            background-color: #f0fff4;
            border-left: 5px solid var(--success-color);
            padding: 1.2rem;
            margin: 1.2rem 0;
            border-radius: 4px;
        }
        
        .button {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            padding: 12px 24px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            margin-top: 10px;
        }
        
        .button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .actions {
            display: flex;
            gap: 15px;
            margin-top: 2rem;
            flex-wrap: wrap;
        }
        
        @media (max-width: 768px) {
            .content {
                padding: 1.5rem;
            }
            
            .steps li {
                padding-right: 2.5rem;
            }
            
            header h1 {
                font-size: 1.8rem;
            }
            
            .actions {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>چارەسەری کێشەی <code>Failed to locate 'package.json'</code></h1>
            <p>ئەم کێشەیە کاتێک ڕوودەدا کە فایلێکی package.json لە پڕۆژەکەتدا نییە یان ڕێگای دروستی پێناسە نەکراوە</p>
        </header>
        
        <div class="content">
            <div class="error-section">
                <h2 class="error-title">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <circle cx="12" cy="12" r="10"></circle>
                        <line x1="12" y1="8" x2="12" y2="12"></line>
                        <line x1="12" y1="16" x2="12.01" y2="16"></line>
                    </svg>
                    هەڵەیەک ڕوویدا
                </h2>
                <p>لە ماڵپەڕی Vercel، هەڵەی <code>Failed to locate 'package.json'</code> بەڕێزەکەت. ئەمە مانای ئەوەیە کە فایلێکی <code>package.json</code> لە پڕۆژەکەتدا نییە یان لە شوێنێکی هەڵەدایە.</p>
            </div>
            
            <div class="solution-section">
                <h2 class="solution-title">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path>
                    </svg>
                    چارەسەرەکان
                </h2>
                
                <ol class="steps">
                    <li>
                        <strong>دڵنیابە لە بوونی فایلی package.json</strong>
                        <p>دڵنیابە لەوەی کە فایلی <code>package.json</code> لە پڕۆژەکەتدا هەیە. ئەم فایلە پێویستە لە ڕەگی پڕۆژەکەتدا بێت.</p>
                        <div class="file-structure">
                            پڕۆژەکەم/<br>
                            ├── package.json  &larr; ئەم فایلە پێویستە لێرە بێت<br>
                            ├── public/<br>
                            ├── src/<br>
                            └── ...
                        </div>
                    </li>
                    
                    <li>
                        <strong>دروستکردنی فایلی package.json ئەگەر نییە</strong>
                        <p>ئەگەر فایلی <code>package.json</code>ت نییە، دەتوانیت بە هۆکاری خوارەوە دروستی بکەیت:</p>
                        <div class="code-block">
{
  "name": "newsytam",
  "version": "1.0.0",
  "description": "My news website",
  "main": "index.js",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^3.1.0",
    "vite": "^4.1.0"
  }
}
                        </div>
                        <p>یان بە بەکارهێنانی فەرمانی <code>npm init</code> لە ترمیناڵ:</p>
                        <div class="code-block">
npm init -y
                        </div>
                    </li>
                    
                    <li>
                        <strong>ڕێگای ڕاست دیاری بکە لە Vercel</strong>
                        <p>لە ڕێگای پەیوەندییەکەت لە Vercel، دڵنیابە لەوەی کە ڕێگای ڕاست دیاری کراوە بۆ فایلی <code>package.json</code>:</p>
                        <div class="note">
                            <p>بچە بۆ پەیوەندییەکەت → Settings → Build & Development Settings</p>
                            <p>دڵنیابە لەوەی کە "Root Directory" بە شێوازی ڕاست دیاری کراوە.</p>
                        </div>
                    </li>
                    
                    <li>
                        <strong>پێکهێنانی Framework Preset</strong>
                        <p>لە Vercel، Framework Preset دیاری بکە بۆ پڕۆژەکەت:</p>
                        <div class="note">
                            <p>بچە بۆ پەیوەندییەکەت → Settings → Framework Preset</p>
                            <p>ئەگەر پڕۆژەکەت Reactە، "Create React App" هەڵبژێرە. ئەگەر Vueە، "Vue" هەڵبژێرە، هتد.</p>
                        </div>
                    </li>
                    
                    <li>
                        <strong>Build Command و Output Directory</strong>
                        <p>دڵنیابە لەوەی کە Build Command و Output Directory بە شێوازی ڕاست دیاری کراوە:</p>
                        <div class="note">
                            <p>Build Command: <code>npm run build</code></p>
                            <p>Output Directory: <code>dist</code> یان <code>build</code> یان <code>out</code> (پەیوەستە بە پڕۆژەکەت)</p>
                        </div>
                    </li>
                </ol>
            </div>
            
            <div class="success-message">
                <h3>پێشنیارێکی زیاتر</h3>
                <p>ئەگەر هێشتا کێشەکەت چارەسەر نەبوو، دەتوانیت پڕۆژەکەت بە شێوازی خوارەوە لە Vercel دیپلۆی بکەیت:</p>
                
                <div class="actions">
                    <a href="#" class="button">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="margin-left: 5px;">
                            <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
                            <polyline points="14 2 14 8 20 8"></polyline>
                            <line x1="16" y1="13" x2="8" y2="13"></line>
                            <line x1="16" y1="17" x2="8" y2="17"></line>
                            <polyline points="10 9 9 9 8 9"></polyline>
                        </svg>
                        دروستکردنی فایلی package.json
                    </a>
                    
                    <a href="#" class="button">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="margin-left: 5px;">
                            <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path>
                            <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path>
                        </svg>
                        سەیرکردنی نموونەی package.json
                    </a>
                    
                    <a href="#" class="button">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="margin-left: 5px;">
                            <circle cx="12" cy="12" r="10"></circle>
                            <line x1="12" y1="8" x2="12" y2="12"></line>
                            <line x1="12" y1="16" x2="12.01" y2="16"></line>
                        </svg>
                        پەیوەندی بە پشتیوانی Vercel
                    </a>
                </div>
            </div>
        </div>
    </div>

    <script>
        // کۆدی جاڤاسکریپت بۆ دروستکردنی فایلەکان
        document.addEventListener('DOMContentLoaded', function() {
            // دروستکردنی فایلی package.json
            document.querySelectorAll('.button')[0].addEventListener('click', function(e) {
                e.preventDefault();
                const packageJsonContent = `{
  "name": "newsytam",
  "version": "1.0.0",
  "description": "My news website",
  "main": "index.js",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^3.1.0",
    "vite": "^4.1.0"
  }
}`;
                
                const blob = new Blob([packageJsonContent], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = 'package.json';
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                
                alert('فایلی package.json داگرتە بە سەرکەوتوویی! ئێستا ئەم فایلە زیاد بکە بە ڕەگی پڕۆژەکەت.');
            });
            
            // سەیرکردنی نموونەی package.json
            document.querySelectorAll('.button')[1].addEventListener('click', function(e) {
                e.preventDefault();
                alert('نموونەی فایلی package.json لە بەشی ٢ی چارەسەرەکان پیشان دراوە. دەتوانیت ئەو نموونەیە کۆپی بکەیت و بۆ پڕۆژەکەت بەکاریبێنیت.');
            });
            
            // پەیوەندی بە پشتیوانی Vercel
            document.querySelectorAll('.button')[2].addEventListener('click', function(e) {
                e.preventDefault();
                window.open('https://vercel.com/contact', '_blank');
            });
        });
    </script>
</body>
</html>
