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
let clickCounter = 0;
const maxClicks = 5;

const shareBtn = document.getElementById('shareBtn');
const clickCount = document.getElementById('clickCount');
const submitBtn = document.getElementById('submitBtn');
const form = document.getElementById('registrationForm');
const message = document.getElementById('message');

// Prevent multiple submissions
if (localStorage.getItem("submitted") === "true") {
  form.querySelectorAll("input, button").forEach(el => el.disabled = true);
  message.textContent = "🎉 Your submission has been recorded. Thanks for being part of Tech for Girls!";
}

shareBtn.addEventListener("click", () => {
  if (clickCounter < maxClicks) {
    clickCounter++;
    clickCount.textContent = `Click Count: ${clickCounter}/${maxClicks}`;
    
    let url = `https://wa.me/?text=Hey%20Buddy,%20Join%20Tech%20For%20Girls%20Community!`;
    window.open(url, "_blank");
    
    if (clickCounter === maxClicks) {
      shareBtn.disabled = true;
      clickCount.textContent = `Sharing complete. Please continue.`;
    }
  }
});

form.addEventListener("submit", async (e) => {
  e.preventDefault();

  if (clickCounter < maxClicks) {
    alert("Please complete WhatsApp sharing first!");
    return;
  }

  const formData = new FormData(form);
  const file = formData.get("screenshot");

  // Upload to Google Drive via Apps Script Web App
  const webAppURL = 'https://script.google.com/macros/s/AKfycbyRExkSCxKphMj5WAvY-vZIFcbIjLgJVseKgtxSvC7RYLrEEy_fJlEqiQ1WIyRe_3In/exec'; // replace this

  const response = await fetch(webAppURL, {
    method: 'POST',
    body: formData,
  });

  if (response.ok) {
    message.textContent = "🎉 Your submission has been recorded. Thanks for being part of Tech for Girls!";
    form.querySelectorAll("input, button").forEach(el => el.disabled = true);
    localStorage.setItem("submitted", "true");
  } else {
    alert("Submission failed. Try again.");
  }
});
