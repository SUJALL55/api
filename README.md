<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Login Page</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #4A90E2, #1A1A2E);
        }
        .login-container {
            background: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            text-align: center;
            width: 350px;
        }
        h2 {
            margin-bottom: 20px;
            color: #333;
        }
        .input-group {
            position: relative;
            margin-bottom: 15px;
            width: 100%;
        }
        .input-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
            outline: none;
            padding-right: 40px;
        }
        .input-group .icon {
            position: absolute;
            right: 10px;
            top: 50%;
            transform: translateY(-50%);
            color: gray;
            cursor: pointer;
        }
        .remember-me {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        .remember-me input {
            margin-right: 8px;
        }
        .error-message {
            color: red;
            font-size: 14px;
            margin-bottom: 10px;
            display: none;
        }
        .login-btn {
            background: #4A90E2;
            color: #fff;
            padding: 12px;
            width: 100%;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
        }
        .login-btn:hover {
            background: #357ABD;
        }
        .forgot-password {
            margin-top: 10px;
            font-size: 14px;
        }
        .forgot-password a {
            color: #4A90E2;
            text-decoration: none;
        }
        .forgot-password a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <h2>Login</h2>
        <div class="error-message" id="error-message"></div>
        <form id="login-form">
            <div class="input-group">
                <input type="email" id="email" placeholder="Email" required>
                <i class="fas fa-envelope icon"></i>
            </div>
            <div class="input-group">
                <input type="password" id="password" placeholder="Password" required>
                <i class="fas fa-eye icon" id="toggle-password"></i>
            </div>
            <div class="remember-me">
                <input type="checkbox" id="remember-me">
                <label for="remember-me">Remember Me</label>
            </div>
            <button type="submit" class="login-btn">Login</button>
        </form>
        <div class="forgot-password">
            <a href="#">Forgot Password?</a>
        </div>
    </div>

    <script>
        // Toggle Password Visibility
        document.getElementById("toggle-password").addEventListener("click", function() {
            let passwordInput = document.getElementById("password");
            if (passwordInput.type === "password") {
                passwordInput.type = "text";
                this.classList.remove("fa-eye");
                this.classList.add("fa-eye-slash");
            } else {
                passwordInput.type = "password";
                this.classList.remove("fa-eye-slash");
                this.classList.add("fa-eye");
            }
        });

        // Login Validation
        document.getElementById("login-form").addEventListener("submit", function(event) {
            event.preventDefault();
            
            let email = document.getElementById("email").value;
            let password = document.getElementById("password").value;
            let errorMessage = document.getElementById("error-message");

            // Email Validation
            let emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                errorMessage.innerText = "Invalid email format!";
                errorMessage.style.display = "block";
                return;
            }

            // Password Validation
            if (password.length < 6) {
                errorMessage.innerText = "Password must be at least 6 characters!";
                errorMessage.style.display = "block";
                return;
            }

            // Successful Login (Here, you can send data to a backend)
            errorMessage.style.display = "none";
            alert("Login Successful!");
        });
    </script>
</body>
</html>
