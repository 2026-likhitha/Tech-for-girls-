Tech for girls
<!DOCTYPE html>
<html lang="me="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tech For Girls Registration</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f9f9f9;
      padding: 20px;<div class="container">
  <h1>Tech for Girls Registration</h1>
  
  <!-- Your form goes here -->

  <button id="whatsappShare">Share on WhatsApp</button>
  <div class="whatsapp-share">
    <p id="shareCount">Shared 0 times</p>
  </div>
</div>
    }

    .container {
      max-width: 500px;
      margin: auto;
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    h1 {
      text-align: center;
      color: #d63384;
    }

    form label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
    }

    form input[type="text"],
    form input[type="email"],
    form input[type="number"],
    form input[type="file"] {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
      margin-top: 20px;
      width: 100%;
      padding: 12px;
      background-color: #20c997;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 16px;
    }

    button:disabled {
      background-color: #6c757d;
    }

    .whatsapp-share p {
      margin-top: 10px;
      font-size: 14px;
    }
    <button id="whatsappShare">Share on WhatsApp</button>
 <div class="whatsapp-share">
  <button id="whatsappShare">Share on WhatsApp</button>
  <p>Click the button to share this on WhatsApp!</p>
</div>
</style>
</head>
<body>
  <div class="container">
    <h1>🚀 Tech For Girls: Registration</h1>

    <form id="registrationForm">
      <label>Name:</label>
      <input type="text" id="name" required />

      <label>Phone Number:</label>
      <input type="number" id="phone" required />

      <label>Email ID:</label>
      <input type="email" id="email" required />

      <label>College/Department:</label>
      <input type="text" id="college" required />

      <div class="whatsapp-share">
        <button type="button" id="whatsappBtn">Share on WhatsApp</button>
        <p id="shareCount">Click count: 0/5</p>
        <p id="shareDoneMsg" style="display:none;">✅ Sharing complete. Please continue.</p>
      </div>

      <br /><br />
      <label for="screenshot">📸 Upload WhatsApp Screenshot:</label><br />
      <input type="file" id="screenshot" name="screenshot" accept="image/*" required /><br />
      <small>Please upload proof of WhatsApp sharing.</small>

      <br /><br />
      <button type="submit" id="submitBtn">Submit Registration</button>
    </form>

    <p id="thankYouMsg" style="display:none;">🎉 Your submission has been recorded. Thanks for being part of Tech for Girls!</p>
  </div>
  <script>
  let shareCount = localStorage.getItem("whatsappShareCount") || 0;
  document.getElementById("shareCount").innerText = `Shared ${shareCount} times`;

  document.getElementById("whatsappShare").addEventListener("click", function () {
    const text = encodeURIComponent("Hey! Register now for the Tech for Girls event.");
    const url = encodeURIComponent(window.location.href); // Current page URL
    const whatsappURL = `https://wa.me/?text=${text}%20${url}`;

    // Open WhatsApp share link
    window.open(whatsappURL, "_blank");

    // Update and store share count
    shareCount++;
    localStorage.setItem("whatsappShareCount", shareCount);
    document.getElementById("shareCount").innerText = `Shared ${shareCount} times`;
  });
</script>

  <script>
    let clickCounter = 0;
    const maxClicks = 5;

    const whatsappBtn = document.getElementById('whatsappBtn');
    const shareCount = document.getElementById('shareCount');
    const shareDoneMsg = document.getElementById('shareDoneMsg');
    const submitBtn = document.getElementById('submitBtn');
    const form = document.getElementById('registrationForm');
    const thankYouMsg = document.getElementById('thankYouMsg');

    // Prevent multiple submissions
    if (localStorage.getItem("submitted") === "true") {
      form.querySelectorAll("input, button").forEach(el => el.disabled = true);
      thankYouMsg.style.display = "block";
    }

    whatsappBtn.addEventListener("click", () => {
      if (clickCounter < maxClicks) {
        clickCounter++;
        shareCount.textContent = `Click count: ${clickCounter}/${maxClicks}`;

        const shareText = encodeURIComponent("Hey Buddy! Join Tech For Girls: https://2026-likhitha.github.io/Tech-for-girls/");
        const url = `https://api.whatsapp.com/send?text=${shareText}`;
        window.open(url, "_blankconst shareText = encodeURIComponent("Hey Buddy! Join Tech For Girls: https://2026-likhitha.github.io/Tech-for-girls/
        if (clickCounter === maxClicks) {
          whatsappBtn.disabled = true;
          shareCount.style.display = "none";
          shareDoneMsg.style.display = "block";
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
      const webAppURL = 'https://script.google.com/macros/s/AKfycbyRExkSCxKphMj5WAvY-vZIFcbIjLgJVseKgtxSvC7RYLrEEy_fJlEqiQ1WIyRe_3In/exec';

      const response = await fetch(webAppURL, {
        method: 'POST',
        body: formData,
      });

      if (response.ok) {
        thankYouMsg.style.display = "block";
        form.querySelectorAll("input, button").forEach(el => el.disabled = true);
        localStorage.setItem("submitted", "true");
      } else {
        alert("Submission failed. Try again.");
      }
    
