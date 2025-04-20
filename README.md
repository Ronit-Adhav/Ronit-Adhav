<!DOCTYPE html>
<html>
<head>
  <title>Login Page</title>
</head>
<body>
  <h2>Login</h2>
  <form id="loginForm">
    <label>Username:</label>
    <input type="text" id="username" required><br><br>
    <label>Password:</label>
    <input type="password" id="password" required><br><br>
    <button type="submit">Login</button>
  </form>

  <script>
    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const username = document.getElementById("username").value;
      const password = document.getElementById("password").value;

      fetch("https://script.google.com/macros/s/AKfycbxP2yaGd6XHDpvbr9MIsAaKemDrYk0dB5zTt6nYjh3b0AqsD6rxhURzXwvb8OJZueUV/exec", {
        method: "POST",
        body: JSON.stringify({ username, password }),
        headers: { "Content-Type": "application/json" }
      })
      .then(res => res.text())
      .then(response => {
        alert("Response from server: " + response);
        document.getElementById("loginForm").reset();
      })
      .catch(err => alert("Error: " + err));
    });
  </script>
</body>
</html>


