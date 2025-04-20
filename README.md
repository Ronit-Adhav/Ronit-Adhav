<!DOCTYPE html>
<html>
<head>
  <title>Login Page</title>
</head>
<body>
  <h2>Login</h2>
  <form id="loginForm">
    <label for="username">Username:</label><br>
    <input type="text" id="username" required><br><br>
    <label for="password">Password:</label><br>
    <input type="password" id="password" required><br><br>
    <button type="submit">Submit</button>
  </form>

  <script>
    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const username = document.getElementById("username").value;
      const password = document.getElementById("password").value;

      fetch("[YOUR_WEB_APP_URL_HERE](https://script.google.com/macros/s/AKfycbwyvJga4XXug4AEmdI3E7r7sAkUQ0v0t0ailX9TYt6jSKDrHRCkj1aRC6KNtdT-fSBz/exec)", {
        method: "POST",
        body: JSON.stringify({ username, password }),
        headers: { "Content-Type": "application/json" }
      })
      .then(response => response.text())
      .then(responseData => {
        alert("Response: " + responseData);
        document.getElementById("loginForm").reset();
      })
      .catch(err => alert("Error: " + err));
    });
  </script>
</body>
</html>
