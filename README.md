# fundmate
A platform to change USDT to INR with QR - based payments
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FundMate - Crypto Funding Platform</title>
    <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding: 40px 0;
        }

        .logo {
            font-size: 3rem;
            font-weight: 800;
            color: white;
            text-shadow: 0 4px 20px rgba(0,0,0,0.3);
            margin-bottom: 10px;
            transform: perspective(1000px) rotateX(15deg);
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: perspective(1000px) rotateX(15deg) translateY(0px); }
            50% { transform: perspective(1000px) rotateX(15deg) translateY(-10px); }
        }

        .subtitle {
            color: rgba(255,255,255,0.9);
            font-size: 1.2rem;
            margin-bottom: 30px;
        }

        .card-3d {
            background: rgba(255,255,255,0.95);
            border-radius: 20px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 
                0 20px 40px rgba(0,0,0,0.1),
                0 0 0 1px rgba(255,255,255,0.2);
            transform: perspective(1000px) rotateX(5deg);
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .card-3d:hover {
            transform: perspective(1000px) rotateX(0deg) translateY(-10px);
            box-shadow: 
                0 30px 60px rgba(0,0,0,0.15),
                0 0 0 1px rgba(255,255,255,0.3);
        }

        .wallet-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin: 40px 0;
        }

        .wallet-card {
            background: linear-gradient(145deg, #f8f9ff, #e8ecff);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            box-shadow: 
                8px 8px 16px rgba(0,0,0,0.1),
                -8px -8px 16px rgba(255,255,255,0.8);
            transition: all 0.3s ease;
        }

        .wallet-card:hover {
            transform: translateY(-5px) scale(1.02);
        }

        .wallet-title {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 15px;
            color: #4c51bf;
        }

        .qr-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
            box-shadow: inset 0 2px 10px rgba(0,0,0,0.1);
        }

        .qr-code {
            width: 200px;
            height: 200px;
            margin: 0 auto;
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            color: #666;
            text-align: center;
            position: relative;
        }

        .address-box {
            background: #f7fafc;
            border: 2px dashed #cbd5e0;
            border-radius: 8px;
            padding: 15px;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
            font-size: 0.9rem;
            word-break: break-all;
            color: #2d3748;
        }

        .copy-btn {
            background: linear-gradient(145deg, #4299e1, #3182ce);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(66, 153, 225, 0.3);
        }

        .copy-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(66, 153, 225, 0.4);
        }

        .help-section {
            background: linear-gradient(145deg, #fff5f5, #fed7d7);
            border-radius: 15px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 
                8px 8px 16px rgba(0,0,0,0.1),
                -8px -8px 16px rgba(255,255,255,0.8);
        }

        .help-title {
            font-size: 2rem;
            font-weight: 700;
            color: #c53030;
            text-align: center;
            margin-bottom: 30px;
        }

        .help-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .help-card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .help-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 35px rgba(0,0,0,0.15);
        }

        .telegram-section {
            text-align: center;
            background: linear-gradient(145deg, #e6fffa, #b2f5ea);
            border-radius: 12px;
            padding: 25px;
        }

        .telegram-qr {
            width: 150px;
            height: 150px;
            margin: 20px auto;
            background: white;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .feature-card {
            background: rgba(255,255,255,0.9);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-5px) rotateY(5deg);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 15px;
        }

        .btn-primary {
            background: linear-gradient(145deg, #48bb78, #38a169);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 6px 20px rgba(72, 187, 120, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(72, 187, 120, 0.4);
        }

        @media (max-width: 768px) {
            .container { padding: 10px; }
            .logo { font-size: 2rem; }
            .wallet-section { grid-template-columns: 1fr; }
            .qr-code { width: 150px; height: 150px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="logo">💰 FundMate</div>
            <div class="subtitle">Your Trusted Crypto Funding Platform</div>
            <button class="btn-primary" onclick="scrollToWallets()">Start Funding</button>
        </div>

        <div class="feature-grid">
            <div class="feature-card">
                <div class="feature-icon">🚀</div>
                <h3>Fast Transactions</h3>
                <p>Lightning-fast crypto transfers with minimal fees</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">🔒</div>
                <h3>Secure Platform</h3>
                <p>Bank-level security for all your transactions</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">🌍</div>
                <h3>Global Access</h3>
                <p>Available worldwide, 24/7 support</p>
            </div>
        </div>

        <div id="wallets" class="wallet-section">
            <div class="card-3d">
                <div class="wallet-card">
                    <div class="wallet-title">🟢 USDT TRC-20</div>
                    <div class="qr-container">
                        <img src="trc20.png" alt="TRC-20QR" width="200" /> 
                                    <img...>
                    <div class="address-box">
                        TRC-20 Address:<br>
                        TWCtpUaW6dzmgi9B2quh3VoxVUmThNLcxR
                    </div>
                    <button class="copy-btn" onclick="copyAddress('TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t')">
                        📋 Copy Address
                    </button>
                </div>
            </div>

            <div class="card-3d">
                <div class="wallet-card">
                    <div class="wallet-title">🟡 BEP-20 (BSC)</div>
                    <div class="qr-container">
                        <img src="bep20.png" alt="BEP-20QR" width="200" />
                            <img...>
                    <div class="address-box">
                        BEP-20 Address:<br>
                        0x4d8322883f4bd1f06e246e940efb2cdd5ed708f8
                    </div>
                    <button class="copy-btn" onclick="copyAddress('0x742d35Cc6634C0532925a3b8D4C9db96C4b4c2bE')">
                        📋 Copy Address
                    </button>
                </div>
            </div>
        </div>

        <div class="help-section">
            <div class="help-title">🆘 Help & Support</div>
            <div class="help-content">
                <div class="help-card">
                    <h3>📚 How to Use FundMate</h3>
                    <ul style="text-align: left; line-height: 1.8;">
                        <li>Choose your preferred cryptocurrency (TRC-20 or BEP-20)</li>
                        <li>Scan the QR code or copy the wallet address</li>
                        <li>Send your funds from your wallet app</li>
                        <li>Transaction will be confirmed within minutes</li>
                        <li>Contact support if you need assistance</li>
                    </ul>
                </div>
                
                <div class="help-card">
                    <h3>⚠ Important Notes</h3>
                    <ul style="text-align: left; line-height: 1.8;">
                        <li>Always double-check the wallet address</li>
                        <li>Only send compatible tokens to each address</li>
                        <li>TRC-20: Send USDT on TRON network</li>
                        <li>BEP-20: Send tokens on Binance Smart Chain</li>
                        <li>Keep transaction receipts for your records</li>
                    </ul>
                </div>
                
                <div class="telegram-section">
                    <h3>💬 Telegram Support</h3>
                    <p>Get instant help from our support team</p>
                    <div class="telegram-qr">
    <p>Scan to message us on Telegram!</p>
