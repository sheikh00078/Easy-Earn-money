<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <title>Eazy to Earn - লগইন / রেজিস্ট্রেশন</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: url('https://i.imgur.com/KnfGxIR.jpg') no-repeat center center fixed;
      background-size: cover;
      margin: 0;
      padding: 0;
    }
    .container {
      width: 350px;
      margin: 80px auto;
      background: rgba(255,255,255,0.95);
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px #00000066;
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    input[type="text"], input[type="password"], input[type="tel"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 12px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      width: 100%;
      padding: 10px;
      background-color: #2196F3;
      border: none;
      color: white;
      font-size: 16px;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #1976D2;
    }
    .toggle-link {
      text-align: center;
      margin-top: 15px;
    }
    .toggle-link a {
      color: #2196F3;
      cursor: pointer;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <div class="container" id="loginForm">
    <h2>লগ ইন করুন</h2>
    <input type="tel" placeholder="মোবাইল নাম্বার" id="loginPhone">
    <input type="password" placeholder="পাসওয়ার্ড" id="loginPassword">
    <button onclick="login()">লগ ইন</button>
    <div class="toggle-link">
      <p>নতুন একাউন্ট? <a onclick="toggleForm()">রেজিস্ট্রেশন করুন</a></p>
    </div>
  </div>

  <div class="container" id="registerForm" style="display: none;">
    <h2>রেজিস্ট্রেশন</h2>
    <input type="text" placeholder="আপনার নাম" id="regName">
    <input type="tel" placeholder="মোবাইল নাম্বার" id="regPhone">
    <input type="password" placeholder="পাসওয়ার্ড" id="regPassword">
    <input type="text" placeholder="রেফার কোড (ঐচ্ছিক)" id="regRefer">
    <button onclick="register()">রেজিস্টার</button>
    <div class="toggle-link">
      <p>আগে একাউন্ট করেছেন? <a onclick="toggleForm()">লগ ইন করুন</a></p>
    </div>
  </div>

  <script>
    function toggleForm() {
      const login = document.getElementById('loginForm');
      const register = document.getElementById('registerForm');
      login.style.display = login.style.display === 'none' ? 'block' : 'none';
      register.style.display = register.style.display === 'none' ? 'block' : 'none';
    }

    function login() {
      const phone = document.getElementById('loginPhone').value;
      const password = document.getElementById('loginPassword').value;
      const user = localStorage.getItem(phone);

      if (!user) {
        alert("এই মোবাইল নাম্বারে কোন একাউন্ট নেই!");
        return;
      }

      const userObj = JSON.parse(user);
      if (userObj.password === password) {
        alert("লগইন সফল!");
        window.location.href = "home.html"; // হোম পেইজে যাবে
      } else {
        alert("ভুল পাসওয়ার্ড!");
      }
    }

    function register() {
      const name = document.getElementById('regName').value;
      const phone = document.getElementById('regPhone').value;
      const password = document.getElementById('regPassword').value;
      const refer = document.getElementById('regRefer').value;

      if (localStorage.getItem(phone)) {
        alert("এই নাম্বার দিয়ে আগেই একাউন্ট করা হয়েছে!");
        return;
      }

      const user = {
        name,
        phone,
        password,
        refer
      };

      localStorage.setItem(phone, JSON.stringify(user));
      alert("রেজিস্ট্রেশন সফল! এখন লগ ইন করুন।");
      toggleForm();
    }
  </script>
</body>
</html># Easy-Earn-money
