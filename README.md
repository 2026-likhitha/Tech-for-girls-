Tech for girls
index.html
style.css
script.js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tech For Girls Registration</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>🚀 Tech For Girls: Registration</h1>

    <form id="registrationForm">
      <label>Name:</label>
      <input type="text" id="name" required>

      <label>Phone Number:</label>
      <input type="number" id="phone" required>

      <label>Email ID:</label>
      <input type="email" id="email" required>

      <label>College/Department:</label>
      <input type="text" id="college" required>

      <div class="whatsapp-share">
        <button type="button" id="whatsappBtn">Share on WhatsApp</button>
        <p id="shareCount">Click count: 0/5</p>
        <p id="shareDoneMsg" style="display:none;">Sharing complete. Please continue.</p>
      </div>

      <label>Upload Screenshot:</label>
      <input type="file" id="screenshot" required>

      <button type="submit" id="submitBtn">Submit Registration</button>
    </form>

    <p id="thankYouMsg" style="display:none;">🎉 Your submission has been recorded. Thanks for being part of Tech for Girls!</p>
  </div>

  <script src="script.js"></script>
</body>
</html> Tech for girls
