<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Signup Page with Email or Phone Signup Option</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap"
    rel="stylesheet"
  />
  <style>
    body {
      font-family: 'Inter', sans-serif;
    }
  </style>
</head>
<body class="bg-gray-50 min-h-screen flex items-center justify-center p-4">
  <div class="w-full max-w-md bg-white rounded-lg shadow-lg p-8">
    <h1 class="text-3xl font-semibold text-center mb-8">Signup</h1>

    <div class="flex justify-center mb-6 space-x-4">
      <button id="emailSignupBtn" class="px-4 py-2 font-semibold rounded-md border border-blue-600 text-blue-600 bg-blue-100 focus:outline-none" aria-pressed="true">Email Signup</button>
      <button id="phoneSignupBtn" class="px-4 py-2 font-semibold rounded-md border border-gray-300 text-gray-700 hover:border-blue-600 hover:text-blue-600 focus:outline-none" aria-pressed="false">Phone Signup</button>
    </div>

    <form id="signupForm" class="space-y-6" novalidate>
      <div>
        <label for="signupName" class="block text-gray-700 font-semibold mb-1">Full Name</label>
        <input
          type="text"
          id="signupName"
          name="signupName"
          required
          class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Enter your full name"
        />
      </div>

      <div id="emailField">
        <label for="signupEmail" class="block text-gray-700 font-semibold mb-1">Email</label>
        <input
          type="email"
          id="signupEmail"
          name="signupEmail"
          required
          class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Enter your email"
        />
      </div>

      <div id="phoneField" class="hidden">
        <label for="signupPhone" class="block text-gray-700 font-semibold mb-1">Phone Number</label>
        <input
          type="tel"
          id="signupPhone"
          name="signupPhone"
          pattern="^\d{10}$"
          class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Enter 10-digit phone number"
        />
      </div>

      <div id="otpSection" class="hidden space-y-4">
        <div>
          <label for="signupOTP" class="block text-gray-700 font-semibold mb-1">Enter OTP</label>
          <input
            type="text"
            id="signupOTP"
            name="signupOTP"
            maxlength="6"
            pattern="^\d{6}$"
            class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
            placeholder="Enter 6-digit OTP"
          />
        </div>
        <button type="button" id="verifyOtpBtn" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2 rounded-md transition-colors duration-200">
          Verify OTP
        </button>
      </div>

      <div>
        <label for="signupPassword" class="block text-gray-700 font-semibold mb-1">Password</label>
        <input
          type="password"
          id="signupPassword"
          name="signupPassword"
          required
          minlength="6"
          class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Enter a password (min 6 characters)"
        />
      </div>

      <div>
        <label for="signupConfirmPassword" class="block text-gray-700 font-semibold mb-1">Confirm Password</label>
        <input
          type="password"
          id="signupConfirmPassword"
          name="signupConfirmPassword"
          required
          minlength="6"
          class="w-full border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Confirm your password"
        />
      </div>

      <button
        type="submit"
        id="signupSubmitBtn"
        class="w-full bg-green-600 hover:bg-green-700 text-white font-semibold py-3 rounded-md transition-colors duration-200 flex items-center justify-center"
      >
        <i class="fas fa-user-plus mr-2"></i> Signup
      </button>
    </form>
  </div>

  <script>
    const emailSignupBtn = document.getElementById('emailSignupBtn');
    const phoneSignupBtn = document.getElementById('phoneSignupBtn');
    const emailField = document.getElementById('emailField');
    const phoneField = document.getElementById('phoneField');
    const otpSection = document.getElementById('otpSection');
    const signupForm = document.getElementById('signupForm');
    const signupSubmitBtn = document.getElementById('signupSubmitBtn');
    const verifyOtpBtn = document.getElementById('verifyOtpBtn');
    const signupOTPInput = document.getElementById('signupOTP');

    let otpVerified = false;
    let generatedOTP = null;

    function activateEmailSignup() {
      emailSignupBtn.classList.add('border-blue-600', 'text-blue-600', 'bg-blue-100');
      emailSignupBtn.classList.remove('border-gray-300', 'text-gray-700', 'bg-white');
      emailSignupBtn.setAttribute('aria-pressed', 'true');

      phoneSignupBtn.classList.remove('border-blue-600', 'text-blue-600', 'bg-blue-100');
      phoneSignupBtn.classList.add('border-gray-300', 'text-gray-700', 'bg-white');
      phoneSignupBtn.setAttribute('aria-pressed', 'false');

      emailField.classList.remove('hidden');
      phoneField.classList.add('hidden');
      otpSection.classList.add('hidden');

      // Set required attributes accordingly
      document.getElementById('signupEmail').required = true;
      document.getElementById('signupPhone').required = false;
      document.getElementById('signupPhone').value = '';
      signupOTPInput.value = '';
      otpVerified = false;
      signupSubmitBtn.disabled = false;
      signupSubmitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
    }

    function activatePhoneSignup() {
      phoneSignupBtn.classList.add('border-blue-600', 'text-blue-600', 'bg-blue-100');
      phoneSignupBtn.classList.remove('border-gray-300', 'text-gray-700', 'bg-white');
      phoneSignupBtn.setAttribute('aria-pressed', 'true');

      emailSignupBtn.classList.remove('border-blue-600', 'text-blue-600', 'bg-blue-100');
      emailSignupBtn.classList.add('border-gray-300', 'text-gray-700', 'bg-white');
      emailSignupBtn.setAttribute('aria-pressed', 'false');

      phoneField.classList.remove('hidden');
      emailField.classList.add('hidden');
      otpSection.classList.remove('hidden');

      // Set required attributes accordingly
      document.getElementById('signupPhone').required = true;
      document.getElementById('signupEmail').required = false;
      document.getElementById('signupEmail').value = '';
      signupOTPInput.value = '';
      otpVerified = false;
      signupSubmitBtn.disabled = true;
      signupSubmitBtn.classList.add('opacity-50', 'cursor-not-allowed');
    }

    emailSignupBtn.addEventListener('click', activateEmailSignup);
    phoneSignupBtn.addEventListener('click', activatePhoneSignup);

    // Default to email signup on load
    activateEmailSignup();

    // Simulate sending OTP
    function sendOTP(phone) {
      generatedOTP = Math.floor(100000 + Math.random() * 900000).toString();
      alert(`Simulated OTP sent to ${phone}: ${generatedOTP}`);
      otpSection.classList.remove('hidden');
      signupSubmitBtn.disabled = true;
      signupSubmitBtn.classList.add('opacity-50', 'cursor-not-allowed');
      otpVerified = false;
    }

    // Verify OTP
    verifyOtpBtn.addEventListener('click', () => {
      const enteredOTP = signupOTPInput.value.trim();
      if (enteredOTP.length !== 6 || !/^\d{6}$/.test(enteredOTP)) {
        alert('Please enter a valid 6-digit OTP.');
        return;
      }
      if (enteredOTP === generatedOTP) {
        alert('OTP verified successfully!');
        otpVerified = true;
        signupSubmitBtn.disabled = false;
        signupSubmitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
        otpSection.classList.add('hidden');
      } else {
        alert('Incorrect OTP. Please try again.');
      }
    });

    // When phone number input loses focus, send OTP if valid
    const signupPhoneInput = document.getElementById('signupPhone');
    signupPhoneInput.addEventListener('blur', () => {
      const phone = signupPhoneInput.value.trim();
      const phoneRegex = /^\d{10}$/;
      if (phoneRegex.test(phone)) {
        sendOTP(phone);
      } else if (phone.length > 0) {
        alert('Please enter a valid 10-digit phone number before requesting OTP.');
        otpSection.classList.add('hidden');
        signupSubmitBtn.disabled = true;
        signupSubmitBtn.classList.add('opacity-50', 'cursor-not-allowed');
      } else {
        otpSection.classList.add('hidden');
        signupSubmitBtn.disabled = true;
        signupSubmitBtn.classList.add('opacity-50', 'cursor-not-allowed');
      }
    });

    signupForm.addEventListener('submit', e => {
      e.preventDefault();
      const name = signupForm.signupName.value.trim();
      const email = signupForm.signupEmail.value.trim();
      const phone = signupForm.signupPhone.value.trim();
      const password = signupForm.signupPassword.value;
      const confirmPassword = signupForm.signupConfirmPassword.value;

      if (!name) {
        alert('Please enter your full name.');
        return;
      }

      if (emailSignupBtn.getAttribute('aria-pressed') === 'true') {
        if (!email) {
          alert('Please enter your email.');
          return;
        }
        // Basic email format check
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailRegex.test(email)) {
          alert('Please enter a valid email address.');
          return;
        }
      } else {
        if (!phone) {
          alert('Please enter your phone number.');
          return;
        }
        const phoneRegex = /^\d{10}$/;
        if (!phoneRegex.test(phone)) {
          alert('Please enter a valid 10-digit phone number.');
          return;
        }
        if (!otpVerified) {
          alert('Please verify your phone number by entering the OTP.');
          return;
        }
      }

      if (!password) {
        alert('Please enter a password.');
        return;
      }
      if (password.length < 6) {
        alert('Password must be at least 6 characters.');
        return;
      }
      if (password !== confirmPassword) {
        alert('Passwords do not match.');
        return;
      }

      if (emailSignupBtn.getAttribute('aria-pressed') === 'true') {
        alert(`Account created for ${name} with email ${email}`);
      } else {
        alert(`Account created for ${name} with phone number ${phone}`);
      }
      signupForm.reset();
      otpSection.classList.add('hidden');
      otpVerified = false;
      signupSubmitBtn.disabled = false;
      signupSubmitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
      activateEmailSignup();
    });
  </script>
</body>
</html>
