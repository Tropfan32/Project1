<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Система безопасности</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Montserrat', sans-serif;
            background: #e0e0e0;
            color: #333;
            margin: 0;
            padding: 0;
        }
        .header {
            background: url('https://source.unsplash.com/1600x900/?security,technology') no-repeat center center/cover;
            height: 450px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
            font-size: 2.5em;
            font-weight: 700;
            padding: 20px;
            text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
        }
        .container {
            max-width: 900px;
            margin: 30px auto;
            background: white;
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        h1, h2, h3 {
            text-align: center;
            color: #007BFF;
        }
        p {
            font-size: 1.3em;
            line-height: 1.7;
            text-align: justify;
        }
        ul {
            list-style: none;
            padding: 0;
        }
        ul li {
            background: #7a5cc5;
            color: white;
            padding: 12px;
            margin: 8px 0;
            border-radius: 6px;
            font-size: 1.1em;
            text-align: center;
        }
        button {
            display: block;
            width: 100%;
            background: #7a5cc5;
            color: white;
            padding: 16px;
            border: none;
            border-radius: 6px;
            font-size: 1.3em;
            cursor: pointer;
            margin-top: 25px;
            transition: 0.3s;
        }
        button:hover {
            background: #5a3ea0;
        }
        input {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 1.1em;
        }
        a {
            color: #007BFF;
            text-decoration: none;
            font-size: 1.3em;
        }
        a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="header">Современные системы безопасности</div>
    
    <div class="container">
        <h1>Защити свой дом и офис</h1>
        <p>Наши системы безопасности обеспечивают надежную защиту и удобное управление. Мы используем передовые технологии для предотвращения угроз и взломов, гарантируя вашему дому и офису максимальный уровень безопасности. Современные решения позволяют мгновенно реагировать на любые подозрительные действия, обеспечивая вам спокойствие и уверенность в каждой минуте.</p>
        
        <h2>Наши преимущества</h2>
        <ul>
            <li>Быстрая установка</li>
            <li>Управление через смартфон</li>
            <li>Высокое качество оборудования</li>
            <li>Круглосуточная безопасность</li>
        </ul>
        
        <button onclick="showOrderForm()">Оформить заказ</button>
        
        <div id="order-section" style="display:none;">
            <h2>Оформление заказа</h2>
            <input type="text" id="name" placeholder="Ваше имя" required>
            <input type="tel" id="phone" placeholder="Ваш телефон" required>
            <input type="text" id="address" placeholder="Адрес установки" required>
            
            <h3>Выберите тип датчика</h3>
            <label>
                <input type="radio" name="sensor" value="PIR"> PIR датчик
            </label>
            <label>
                <input type="radio" name="sensor" value="Laser"> Лазерный датчик
            </label>
            
            <button onclick="submitOrder()">Оформить заказ</button>
        </div>
        
        <div id="payment-section" style="display:none;">
            <h3>Ссылка для оплаты</h3>
            <p><a id="kaspi-link" href="https://kaspi.kz/" target="_blank">Оплатить через Kaspi</a></p>
        </div>
    </div>
    
    <script>
        function showOrderForm() {
            document.getElementById("order-section").style.display = "block";
        }
        
        function submitOrder() {
            const name = document.getElementById("name").value;
            const phone = document.getElementById("phone").value;
            const address = document.getElementById("address").value;
            const sensor = document.querySelector('input[name="sensor"]:checked')?.value;
            
            if (name && phone && address && sensor) {
                document.getElementById("order-section").style.display = "none";
                document.getElementById("payment-section").style.display = "block";
                
                const botToken = "7758820685:AAFOwcmV85ePy2jHci0BaFeF4_Fe5oZlYkA";
                const chatId = "6620454832";
                const message = `Новый заказ! Имя: ${name} Телефон: ${phone} Адрес: ${address} Датчик: ${sensor}`;
                
                fetch(`https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatId}&text=${message}`);
            } else {
                alert("Пожалуйста, заполните все поля");
            }
        }
    </script>
</body>
</html>
