# Create-a-Contact-Form-and-Validate-Inuputs-using-JavaScript
Build a contact form with client-side validation for name, email, and message.

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contact Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .contact-form {
      background: #fff;
      padding: 20px 30px;
      border-radius: 10px;
      box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
      width: 350px;
    }
    .contact-form h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    .contact-form label {
      font-weight: bold;
      display: block;
      margin-bottom: 5px;
    }
    .contact-form input,
    .contact-form textarea {
      width: 100%;
      padding: 8px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 14px;
    }
    .contact-form button {
      width: 100%;
      padding: 10px;
      background: #007bff;
      color: #fff;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }
    .contact-form button:hover {
      background: #0056b3;
    }
    .error {
      color: red;
      font-size: 13px;
      margin-bottom: 10px;
    }
    .success {
      color: green;
      font-size: 14px;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="contact-form">
    <h2>Contact Us</h2>
    <form id="contactForm">
      <label for="name">Name</label>
      <input type="text" id="name" placeholder="Enter your name">
      <div id="nameError" class="error"></div>

      <label for="email">Email</label>
      <input type="email" id="email" placeholder="Enter your email">
      <div id="emailError" class="error"></div>

      <label for="message">Message</label>
      <textarea id="message" rows="4" placeholder="Enter your message"></textarea>
      <div id="messageError" class="error"></div>

      <button type="submit">Submit</button>
    </form>
    <div id="successMessage" class="success"></div>
  </div>

  <script>
    const form = document.getElementById("contactForm");
    const name = document.getElementById("name");
    const email = document.getElementById("email");
    const message = document.getElementById("message");

    const nameError = document.getElementById("nameError");
    const emailError = document.getElementById("emailError");
    const messageError = document.getElementById("messageError");
    const successMessage = document.getElementById("successMessage");

    form.addEventListener("submit", function(e) {
      e.preventDefault(); // prevent form from submitting

      let valid = true;
      nameError.textContent = "";
      emailError.textContent = "";
      messageError.textContent = "";
      successMessage.textContent = "";

      // Name validation
      if (name.value.trim() === "") {
        nameError.textContent = "Name is required.";
        valid = false;
      }

      // Email validation
      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (email.value.trim() === "") {
        emailError.textContent = "Email is required.";
        valid = false;
      } else if (!email.value.match(emailPattern)) {
        emailError.textContent = "Enter a valid email.";
        valid = false;
      }

      // Message validation
      if (message.value.trim().length < 10) {
        messageError.textContent = "Message must be at least 10 characters long.";
        valid = false;
      }

      // Success message
      if (valid) {
        successMessage.textContent = "Form submitted successfully!";
        form.reset();
      }
    });
  </script>

</body>
</html>
