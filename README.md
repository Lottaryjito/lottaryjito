<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LuckyWin - Online Lottery System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #0f9b0f);
            color: #fff;
            min-height: 100vh;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }
        
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 10% 20%, rgba(255, 255, 255, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 80% 70%, rgba(255, 255, 255, 0.1) 0%, transparent 20%);
            pointer-events: none;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
            z-index: 2;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            margin-bottom: 30px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo i {
            font-size: 2.8rem;
            color: #FFD700;
            animation: pulse 2s infinite;
        }
        
        .logo h1 {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(to right, #FFD700, #FFFFFF);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }
        
        .user-controls {
            display: flex;
            gap: 20px;
            align-items: center;
        }
        
        .btn {
            padding: 12px 30px;
            border-radius: 50px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: linear-gradient(to right, #FF512F, #F09819);
            color: white;
            box-shadow: 0 5px 20px rgba(240, 152, 25, 0.4);
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(240, 152, 25, 0.6);
        }
        
        .btn-outline {
            background: transparent;
            border: 2px solid #FFD700;
            color: #FFD700;
        }
        
        .btn-outline:hover {
            background: rgba(255, 215, 0, 0.1);
        }
        
        .hero {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 40px 0;
            margin-bottom: 40px;
            position: relative;
        }
        
        .hero-content {
            flex: 1;
            max-width: 600px;
        }
        
        .hero-content h2 {
            font-size: 3.8rem;
            line-height: 1.2;
            margin-bottom: 20px;
            background: linear-gradient(to right, #ffffff, #FFD700);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 15px rgba(0, 0, 0, 0.2);
        }
        
        .hero-content p {
            font-size: 1.3rem;
            opacity: 0.9;
            margin-bottom: 30px;
            line-height: 1.7;
        }
        
        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
            position: relative;
        }
        
        .hero-image img {
            max-width: 100%;
            height: auto;
            border-radius: 20px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
            animation: float 4s ease-in-out infinite;
        }
        
        .countdown {
            background: rgba(0, 0, 0, 0.25);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin: 40px 0;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .countdown h3 {
            font-size: 2rem;
            margin-bottom: 20px;
            color: #FFD700;
        }
        
        .timer {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        
        .timer-item {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 20px;
            min-width: 110px;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }
        
        .timer-value {
            font-size: 3rem;
            font-weight: 800;
            color: #FFD700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }
        
        .timer-label {
            font-size: 1.1rem;
            opacity: 0.8;
            margin-top: 5px;
        }
        
        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin: 60px 0 40px;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(to right, #ffffff, #FFD700);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 5px;
            background: #FFD700;
            border-radius: 3px;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
        }
        
        .card-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
            margin-bottom: 60px;
        }
        
        .card {
            background: rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            transition: transform 0.4s ease, box-shadow 0.4s ease;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.25);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .card:hover {
            transform: translateY(-15px);
            box-shadow: 0 20px 45px rgba(0, 0, 0, 0.4);
        }
        
        .card-header {
            background: linear-gradient(135deg, #8E2DE2, #4A00E0);
            padding: 25px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .card-header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(30deg);
        }
        
        .card-body {
            padding: 30px;
        }
        
        .lottery-name {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 10px;
            position: relative;
            z-index: 2;
        }
        
        .lottery-price {
            font-size: 1.8rem;
            color: #FFD700;
            margin-bottom: 15px;
            position: relative;
            z-index: 2;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.4);
        }
        
        .lottery-details {
            margin: 20px 0;
        }
        
        .detail-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .ticket-controls {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
        }
        
        .quantity-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: none;
            background: linear-gradient(to right, #FF512F, #F09819);
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 5px 15px rgba(240, 152, 25, 0.3);
            transition: all 0.2s ease;
        }
        
        .quantity-btn:active {
            transform: scale(0.95);
        }
        
        .ticket-quantity {
            font-size: 1.8rem;
            min-width: 60px;
            text-align: center;
            font-weight: 700;
            color: #FFD700;
        }
        
        .winner-list {
            list-style-type: none;
        }
        
        .winner-item {
            display: flex;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .winner-item:last-child {
            border-bottom: none;
        }
        
        .winner-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, #8E2DE2, #4A00E0);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 20px;
            font-size: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .winner-info {
            flex: 1;
        }
        
        .winner-name {
            font-weight: 700;
            margin-bottom: 5px;
            font-size: 1.2rem;
        }
        
        .winner-prize {
            color: #FFD700;
            font-weight: 600;
            font-size: 1.1rem;
        }
        
        .result-numbers {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin: 30px 0;
        }
        
        .result-number {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: linear-gradient(135deg, #FF512F, #F09819);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            font-weight: 800;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
            animation: pulse 1.5s infinite;
        }
        
        .how-to-play {
            background: rgba(0, 0, 0, 0.25);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 50px;
            margin: 60px 0;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-top: 40px;
        }
        
        .step {
            text-align: center;
            padding: 30px;
            background: rgba(0, 0, 0, 0.15);
            border-radius: 20px;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .step:hover {
            transform: translateY(-10px);
            background: rgba(0, 0, 0, 0.25);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }
        
        .step-icon {
            font-size: 3.5rem;
            margin-bottom: 25px;
            color: #FFD700;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
        }
        
        .step-title {
            font-size: 1.7rem;
            margin-bottom: 20px;
            color: #FFD700;
        }
        
        footer {
            text-align: center;
            padding: 40px 0;
            margin-top: 60px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .social-icons {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin: 30px 0;
        }
        
        .social-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            transition: all 0.3s ease;
            color: #FFD700;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }
        
        .social-icon:hover {
            background: linear-gradient(135deg, #FF512F, #F09819);
            color: white;
            transform: translateY(-8px);
            box-shadow: 0 10px 25px rgba(240, 152, 25, 0.4);
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(to right, #00b09b, #96c93d);
            color: white;
            padding: 15px 30px;
            border-radius: 10px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            transform: translateX(150%);
            transition: transform 0.5s ease;
            z-index: 1000;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }
        
        @media (max-width: 768px) {
            .hero {
                flex-direction: column;
                text-align: center;
            }
            
            .hero-content {
                margin-bottom: 40px;
            }
            
            .timer {
                flex-wrap: wrap;
            }
            
            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-trophy"></i>
                <h1>LuckyWin</h1>
            </div>
            <div class="user-controls">
                <button class="btn btn-outline"><i class="fas fa-user"></i> Login</button>
                <button class="btn btn-primary"><i class="fas fa-user-plus"></i> Register</button>
            </div>
        </header>
        
        <section class="hero">
            <div class="hero-content">
                <h2>Win Big with LuckyWin Lottery!</h2>
                <p>Buy multiple lottery tickets for your chance to win huge cash prizes. Choose from our daily, weekly and mega jackpot lotteries. Purchase as many tickets as you want to increase your winning chances!</p>
                <button class="btn btn-primary"><i class="fas fa-ticket-alt"></i> Buy Tickets Now</button>
            </div>
            <div class="hero-image">
                <img src="https://images.unsplash.com/photo-1620410257516-ae6a28b5d0b8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=600&q=80" alt="Lottery Tickets">
            </div>
        </section>
        
        <section class="countdown">
            <h3>Next Mega Draw In:</h3>
            <div class="timer">
                <div class="timer-item">
                    <div class="timer-value" id="days">02</div>
                    <div class="timer-label">Days</div>
                </div>
                <div class="timer-item">
                    <div class="timer-value" id="hours">18</div>
                    <div class="timer-label">Hours</div>
                </div>
                <div class="timer-item">
                    <div class="timer-value" id="minutes">45</div>
                    <div class="timer-label">Minutes</div>
                </div>
                <div class="timer-item">
                    <div class="timer-value" id="seconds">30</div>
                    <div class="timer-label">Seconds</div>
                </div>
            </div>
        </section>
        
        <h2 class="section-title">Available Lotteries</h2>
        <div class="card-container">
            <div class="card">
                <div class="card-header">
                    <h3 class="lottery-name">Mega Jackpot</h3>
                    <div class="lottery-price">₹500 per ticket</div>
                    <p>Jackpot: ₹5 Crores</p>
                </div>
                <div class="card-body">
                    <div class="lottery-details">
                        <div class="detail-item">
                            <span><i class="fas fa-calendar"></i> Draw Date:</span>
                            <span>July 20, 2025</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-ticket"></i> Tickets Sold:</span>
                            <span>24,587</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-user"></i> Your Tickets:</span>
                            <span>0</span>
                        </div>
                    </div>
                    
                    <div class="ticket-controls">
                        <button class="quantity-btn" onclick="adjustQuantity('mega', -1)"><i class="fas fa-minus"></i></button>
                        <span class="ticket-quantity" id="mega-qty">0</span>
                        <button class="quantity-btn" onclick="adjustQuantity('mega', 1)"><i class="fas fa-plus"></i></button>
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%; padding: 15px;" onclick="buyTickets('mega')">
                        <i class="fas fa-shopping-cart"></i> Buy Tickets
                    </button>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3 class="lottery-name">Weekly Fortune</h3>
                    <div class="lottery-price">₹200 per ticket</div>
                    <p>Jackpot: ₹1 Crore</p>
                </div>
                <div class="card-body">
                    <div class="lottery-details">
                        <div class="detail-item">
                            <span><i class="fas fa-calendar"></i> Draw Date:</span>
                            <span>Every Sunday</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-ticket"></i> Tickets Sold:</span>
                            <span>15,342</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-user"></i> Your Tickets:</span>
                            <span>0</span>
                        </div>
                    </div>
                    
                    <div class="ticket-controls">
                        <button class="quantity-btn" onclick="adjustQuantity('weekly', -1)"><i class="fas fa-minus"></i></button>
                        <span class="ticket-quantity" id="weekly-qty">0</span>
                        <button class="quantity-btn" onclick="adjustQuantity('weekly', 1)"><i class="fas fa-plus"></i></button>
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%; padding: 15px;" onclick="buyTickets('weekly')">
                        <i class="fas fa-shopping-cart"></i> Buy Tickets
                    </button>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3 class="lottery-name">Daily Luck</h3>
                    <div class="lottery-price">₹100 per ticket</div>
                    <p>Jackpot: ₹10 Lakhs</p>
                </div>
                <div class="card-body">
                    <div class="lottery-details">
                        <div class="detail-item">
                            <span><i class="fas fa-calendar"></i> Draw Date:</span>
                            <span>Daily at 8 PM</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-ticket"></i> Tickets Sold:</span>
                            <span>8,456</span>
                        </div>
                        <div class="detail-item">
                            <span><i class="fas fa-user"></i> Your Tickets:</span>
                            <span>0</span>
                        </div>
                    </div>
                    
                    <div class="ticket-controls">
                        <button class="quantity-btn" onclick="adjustQuantity('daily', -1)"><i class="fas fa-minus"></i></button>
                        <span class="ticket-quantity" id="daily-qty">0</span>
                        <button class="quantity-btn" onclick="adjustQuantity('daily', 1)"><i class="fas fa-plus"></i></button>
                    </div>
                    
                    <button class="btn btn-primary" style="width: 100%; padding: 15px;" onclick="buyTickets('daily')">
                        <i class="fas fa-shopping-cart"></i> Buy Tickets
                    </button>
                </div>
            </div>
        </div>
        
        <h2 class="section-title">Latest Winners</h2>
        <div class="card-container">
            <div class="card">
                <div class="card-header">
                    <h3>Recent Winners</h3>
                </div>
                <div class="card-body">
                    <ul class="winner-list">
                        <li class="winner-item">
                            <div class="winner-avatar">
                                <i class="fas fa-crown"></i>
                            </div>
                            <div class="winner-info">
                                <div class="winner-name">Rajesh Kumar</div>
                                <div class="winner-prize">Won ₹1,20,00,000 in Mega Jackpot</div>
                            </div>
                        </li>
                        <li class="winner-item">
                            <div class="winner-avatar">
                                <i class="fas fa-crown"></i>
                            </div>
                            <div class="winner-info">
                                <div class="winner-name">Priya Sharma</div>
                                <div class="winner-prize">Won ₹25,00,000 in Weekly Fortune</div>
                            </div>
                        </li>
                        <li class="winner-item">
                            <div class="winner-avatar">
                                <i class="fas fa-crown"></i>
                            </div>
                            <div class="winner-info">
                                <div class="winner-name">Amit Patel</div>
                                <div class="winner-prize">Won ₹5,00,000 in Daily Luck</div>
                            </div>
                        </li>
                        <li class="winner-item">
                            <div class="winner-avatar">
                                <i class="fas fa-crown"></i>
                            </div>
                            <div class="winner-info">
                                <div class="winner-name">Sneha Gupta</div>
                                <div class="winner-prize">Won ₹15,00,000 in Weekly Fortune</div>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3>Last Draw Results</h3>
                </div>
                <div class="card-body">
                    <h4>Mega Jackpot - July 10, 2025</h4>
                    <div class="result-numbers">
                        <div class="result-number">7</div>
                        <div class="result-number">15</div>
                        <div class="result-number">22</div>
                        <div class="result-number">34</div>
                        <div class="result-number">41</div>
                        <div class="result-number">49</div>
                    </div>
                    
                    <h4 style="margin-top: 40px;">Weekly Fortune - July 10, 2025</h4>
                    <div class="result-numbers">
                        <div class="result-number">5</div>
                        <div class="result-number">12</div>
                        <div class="result-number">19</div>
                        <div class="result-number">27</div>
                        <div class="result-number">33</div>
                    </div>
                    
                    <h4 style="margin-top: 40px;">Daily Luck - July 16, 2025</h4>
                    <div class="result-numbers">
                        <div class="result-number">8</div>
                        <div class="result-number">14</div>
                        <div class="result-number">21</div>
                    </div>
                </div>
            </div>
        </div>
        
        <h2 class="section-title">How to Play</h2>
        <div class="how-to-play">
            <div class="steps">
                <div class="step">
                    <div class="step-icon">
                        <i class="fas fa-user-plus"></i>
                    </div>
                    <h3 class="step-title">Create Account</h3>
                    <p>Register with your details to get started</p>
                </div>
                
                <div class="step">
                    <div class="step-icon">
                        <i class="fas fa-ticket-alt"></i>
                    </div>
                    <h3 class="step-title">Buy Tickets</h3>
                    <p>Select lottery and purchase multiple tickets</p>
                </div>
                
                <div class="step">
                    <div class="step-icon">
                        <i class="fas fa-dice"></i>
                    </div>
                    <h3 class="step-title">Get Numbers</h3>
                    <p>Receive unique lottery numbers instantly</p>
                </div>
                
                <div class="step">
                    <div class="step-icon">
                        <i class="fas fa-trophy"></i>
                    </div>
                    <h3 class="step-title">Check Results</h3>
                    <p>See if you won when the draw happens</p>
                </div>
            </div>
        </div>
        
        <footer>
            <div class="logo" style="justify-content: center; margin-bottom: 30px;">
                <i class="fas fa-trophy"></i>
                <h1>LuckyWin</h1>
            </div>
            <p>Play responsibly. Must be 18+ to participate.</p>
            <div class="social-icons">
                <a href="#" class="social-icon"><i class="fab fa-facebook-f"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-twitter"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-instagram"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-whatsapp"></i></a>
            </div>
            <p style="margin-top: 30px;">&copy; 2025 LuckyWin Lottery. All rights reserved.</p>
        </footer>
    </div>

    <div class="notification" id="notification">
        <i class="fas fa-check-circle"></i> Tickets purchased successfully!
    </div>

    <script>
        // Ticket quantity adjustment
        function adjustQuantity(lottery, change) {
            const qtyElement = document.getElementById(`${lottery}-qty`);
            let currentQty = parseInt(qtyElement.textContent) || 0;
            currentQty += change;
            
            if (currentQty < 0) currentQty = 0;
            if (currentQty > 20) {
                currentQty = 20;
                showNotification("Maximum 20 tickets per purchase");
            }
            
            qtyElement.textContent = currentQty;
        }
        
        // Simulate ticket purchase
        function buyTickets(lottery) {
            const qtyElement = document.getElementById(`${lottery}-qty`);
            const qty = parseInt(qtyElement.textContent);
            
            if (qty > 0) {
                showNotification(`Success! Purchased ${qty} ${lottery} tickets`);
                qtyElement.textContent = "0";
            } else {
                showNotification("Please select at least one ticket");
            }
        }
        
        // Show notification
        function showNotification(message) {
            const notification = document.getElementById('notification');
            notification.innerHTML = `<i class="fas fa-check-circle"></i> ${message}`;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        // Countdown timer
        function updateCountdown() {
            const now = new Date();
            const nextDraw = new Date(now);
            nextDraw.setDate(now.getDate() + 2);
            nextDraw.setHours(20, 0, 0, 0);
            
            const diff = nextDraw - now;
            
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            
            document.getElementById('days').textContent = days.toString().padStart(2, '0');
            document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
        }
        
        // Initialize countdown
        updateCountdown();
        setInterval(updateCountdown, 1000);
    </script>
</body>
</html>

<!--
**Lottaryjito/lottaryjito** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
