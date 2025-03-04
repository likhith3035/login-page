# login-page
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Enhanced Login Form</title>
  <style>
    /* Base Styles */
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: linear-gradient(135deg, #ece9e6, #ffffff);
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
        Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    }
    /* Fade in animation for container */
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    /* Form container */
    .form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      background-color: #ffffff;
      padding: 40px;
      width: 400px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      animation: fadeInUp 0.6s ease-out;
      position: relative;
    }
    ::placeholder {
      font-family: inherit;
      color: #999;
    }
    .flex-column > label {
      color: #333;
      font-weight: 600;
      margin-bottom: 5px;
    }
    .inputForm {
      border: 1.5px solid #ececec;
      border-radius: 10px;
      height: 50px;
      display: flex;
      align-items: center;
      padding: 0 10px;
      transition: border 0.2s ease-in-out;
    }
    .input {
      margin-left: 10px;
      border: none;
      width: 100%;
      height: 100%;
      font-size: 16px;
      color: #333;
    }
    .input:focus {
      outline: none;
    }
    .inputForm:focus-within {
      border-color: #2d79f3;
    }
    .flex-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 14px;
    }
    .flex-row > div > label {
      color: #333;
      font-weight: 400;
    }
    .span {
      color: #2d79f3;
      font-weight: 500;
      cursor: pointer;
      text-decoration: underline;
    }
    .button-submit {
      margin: 20px 0 10px 0;
      background-color: #2d79f3;
      border: none;
      color: white;
      font-size: 16px;
      font-weight: 600;
      border-radius: 10px;
      height: 50px;
      width: 100%;
      cursor: pointer;
      transition: background-color 0.2s ease-in-out, transform 0.1s ease-in-out;
    }
    .button-submit:hover {
      background-color: #1b5bbf;
      transform: scale(1.02);
    }
    .p {
      text-align: center;
      color: #333;
      font-size: 14px;
      margin: 5px 0;
    }
    .btn {
      margin-top: 10px;
      width: 100%;
      height: 50px;
      border-radius: 10px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: 500;
      gap: 10px;
      border: 1px solid #ededed;
      background-color: white;
      cursor: pointer;
      transition: border-color 0.2s ease-in-out, box-shadow 0.2s ease-in-out, transform 0.1s ease-in-out;
    }
    .btn:hover {
      border-color: #2d79f3;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      transform: scale(1.02);
    }
    /* Continue as Guest Button */
    .guest-btn {
      background: none;
      border: none;
      color: #2d79f3;
      cursor: pointer;
      font-size: 14px;
      text-decoration: underline;
      margin-top: 10px;
      transition: color 0.2s ease;
    }
    .guest-btn:hover {
      color: #1b5bbf;
    }
    /* Modal styles (shared for Terms and Guest) */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
    .modal-content {
      background: #fff;
      padding: 30px;
      border-radius: 10px;
      max-width: 600px;
      width: 90%;
      max-height: 80vh;
      overflow-y: auto;
      animation: fadeInUp 0.5s ease-out;
      position: relative;
    }
    .close-modal {
      position: absolute;
      top: 15px;
      right: 15px;
      cursor: pointer;
      font-size: 22px;
      color: #333;
    }
    .modal h2 {
      margin-top: 0;
      text-align: center;
    }
    .terms-text {
      font-size: 14px;
      color: #555;
      line-height: 1.6;
      margin-top: 10px;
    }
    /* Guest Modal Form Fields */
    .modal .guest-field {
      margin: 15px 0;
      display: flex;
      flex-direction: column;
    }
    .modal .guest-field label {
      font-weight: 600;
      margin-bottom: 5px;
      color: #333;
    }
    .modal .guest-field input {
      padding: 10px;
      border: 1px solid #ececec;
      border-radius: 8px;
      font-size: 16px;
      outline: none;
      transition: border 0.2s ease-in-out;
    }
    .modal .guest-field input:focus {
      border-color: #2d79f3;
    }
  </style>
</head>
<body>
  <!-- Enhanced Login Form -->
  <form class="form" id="loginForm">
    <!-- Email Field -->
    <div class="flex-column">
      <label for="email">Email</label>
    </div>
    <div class="inputForm">
      <!-- Email icon -->
      <svg height="20" viewBox="0 0 32 32" width="20" xmlns="http://www.w3.org/2000/svg">
        <g id="Layer_3" data-name="Layer 3">
          <path d="m30.853 13.87a15 15 0 0 0 -29.729 4.082 15.1 15.1 0 0 0 12.876 12.918 15.6 15.6 0 0 0 2.016.13 14.85 14.85 0 0 0 7.715-2.145 1 1 0 1 0 -1.031-1.711 13.007 13.007 0 1 1 5.458-6.529 2.149 2.149 0 0 1 -4.158-.759v-10.856a1 1 0 0 0 -2 0v1.726a8 8 0 1 0 .2 10.325 4.135 4.135 0 0 0 7.83.274 15.2 15.2 0 0 0 .823-7.455zm-14.853 8.13a6 6 0 1 1 6-6 6.006 6.006 0 0 1 -6 6z"></path>
        </g>
      </svg>
      <input type="text" class="input" id="email" placeholder="Enter your Email" required>
    </div>
    
    <!-- Password Field -->
    <div class="flex-column">
      <label for="password">Password</label>
    </div>
    <div class="inputForm">
      <!-- Lock icon -->
      <svg height="20" viewBox="-64 0 512 512" width="20" xmlns="http://www.w3.org/2000/svg">
        <path d="m336 512h-288c-26.453125 0-48-21.523438-48-48v-224c0-26.476562 21.546875-48 48-48h288c26.453125 0 48 21.523438 48 48v224c0 26.476562-21.546875 48-48 48zm-288-288c-8.8125 0-16 7.167969-16 16v224c0 8.832031 7.1875 16 16 16h288c8.8125 0 16-7.167969 16-16v-224c0-8.832031-7.1875-16-16-16zm0 0"></path>
        <path d="m304 224c-8.832031 0-16-7.167969-16-16v-80c0-52.929688-43.070312-96-96-96s-96 43.070312-96 96v80c0 8.832031-7.167969 16-16 16s-16-7.167969-16-16v-80c0-70.59375 57.40625-128 128-128s128 57.40625 128 128v80c0 8.832031-7.167969 16-16 16zm0 0"></path>
      </svg>
      <input type="password" class="input" id="password" placeholder="Enter your Password" required>
      <!-- Eye icon for toggling password visibility -->
      <svg id="togglePassword" viewBox="0 0 576 512" height="20" style="cursor: pointer;" xmlns="http://www.w3.org/2000/svg">
        <path d="M288 32c-80.8 0-145.5 36.8-192.6 80.6C48.6 156 17.3 208 2.5 243.7c-3.3 7.9-3.3 16.7 0 24.6C17.3 304 48.6 356 95.4 399.4C142.5 443.2 207.2 480 288 480s145.5-36.8 192.6-80.6c46.8-43.5 78.1-95.4 93-131.1c3.3-7.9 3.3-16.7 0-24.6c-14.9-35.7-46.2-87.7-93-131.1C433.5 68.8 368.8 32 288 32zM144 256a144 144 0 1 1 288 0 144 144 0 1 1 -288 0zm144-64c0 35.3-28.7 64-64 64c-7.1 0-13.9-1.2-20.3-3.3c-5.5-1.8-11.9 1.6-11.7 7.4c.3 6.9 1.3 13.8 3.2 20.7c13.7 51.2 66.4 81.6 117.6 67.9s81.6-66.4 67.9-117.6c-11.1-41.5-47.8-69.4-88.6-71.1c-5.8-.2-9.2 6.1-7.4 11.7c2.1 6.4 3.3 13.2 3.3 20.3z"></path>
      </svg>
    </div>
    
    <!-- Remember and Forgot -->
    <div class="flex-row">
      <div>
        <input type="checkbox" id="remember">
        <label for="remember">Remember me</label>
      </div>
      <span class="span" id="forgotPassword">Forgot password?</span>
    </div>
    
    <!-- Sign In Button -->
    <button class="button-submit" type="submit">Sign In</button>
    <p class="p">Don't have an account? <span class="span" id="signUp">Sign Up</span></p>
    
    <!-- Social Login -->
    <p class="p">Or Sign In with</p>
    <div class="flex-row">
      <button class="btn google" type="button" id="googleLogin">
        <svg version="1.1" width="20" id="Layer_1" xmlns="http://www.w3.org/2000/svg" 
             xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" 
             viewBox="0 0 512 512" style="enable-background:new 0 0 512 512;" xml:space="preserve">
          <path style="fill:#FBBB00;" d="M113.47,309.408L95.648,375.94l-65.139,1.378C11.042,341.211,0,299.9,0,256
            c0-42.451,10.324-82.483,28.624-117.732h0.014l57.992,10.632l25.404,57.644c-5.317,15.501-8.215,32.141-8.215,49.456
            C103.821,274.792,107.225,292.797,113.47,309.408z"></path>
          <path style="fill:#518EF8;" d="M507.527,208.176C510.467,223.662,512,239.655,512,256c0,18.328-1.927,36.206-5.598,53.451
            c-12.462,58.683-45.025,109.925-90.134,146.187l-0.014-0.014l-73.044-3.727l-10.338-64.535
            c29.932-17.554,53.324-45.025,65.646-77.911h-136.89V208.176h138.887L507.527,208.176L507.527,208.176z"></path>
          <path style="fill:#28B446;" d="M416.253,455.624l0.014,0.014C372.396,490.901,316.666,512,256,512
            c-97.491,0-182.252-54.491-225.491-134.681l82.961-67.91c21.619,57.698,77.278,98.771,142.53,98.771
            c28.047,0,54.323-7.582,76.87-20.818L416.253,455.624z"></path>
          <path style="fill:#F14336;" d="M419.404,58.936l-82.933,67.896c-23.335-14.586-50.919-23.012-80.471-23.012
            c-66.729,0-123.429,42.957-143.965,102.724l-83.397-68.276h-0.014C71.23,56.123,157.06,0,256,0
            C318.115,0,375.068,22.126,419.404,58.936z"></path>
        </svg>
        Google 
      </button>
      <button class="btn apple" type="button" id="appleLogin">
        <svg version="1.1" height="20" width="20" id="Capa_1" xmlns="http://www.w3.org/2000/svg" 
             xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" 
             viewBox="0 0 22.773 22.773" style="enable-background:new 0 0 22.773 22.773;" xml:space="preserve">
          <g>
            <g>
              <path d="M15.769,0c0.053,0,0.106,0,0.162,0c0.13,1.606-0.483,2.806-1.228,3.675c-0.731,0.863-1.732,1.7-3.351,1.573 c-0.108-1.583,0.506-2.694,1.25-3.561C13.292,0.879,14.557,0.16,15.769,0z"></path>
              <path d="M20.67,16.716c0,0.016,0,0.03,0,0.045c-0.455,1.378-1.104,2.559-1.896,3.655c-0.723,0.995-1.609,2.334-3.191,2.334 c-1.367,0-2.275-0.879-3.676-0.903c-1.482-0.024-2.297,0.735-3.652,0.926c-0.155,0-0.31,0-0.462,0 c-0.995-0.144-1.798-0.932-2.383-1.642c-1.725-2.098-3.058-4.808-3.306-8.276c0-0.34,0-0.679,0-1.019 c0.105-2.482,1.311-4.5,2.914-5.478c0.846-0.52,2.009-0.963,3.304-0.765c0.555,0.086,1.122,0.276,1.619,0.464 c0.471,0.181,1.06,0.502,1.618,0.485c0.378-0.011,0.754-0.208,1.135-0.347c1.116-0.403,2.21-0.865,3.652-0.648 c1.733,0.262,2.963,1.032,3.723,2.22c-1.466,0.933-2.625,2.339-2.427,4.74C17.818,14.688,19.086,15.964,20.67,16.716z"></path>
            </g>
          </g>
        </svg>
        Apple 
      </button>
    </div>
    
    <!-- Continue as Guest -->
    <button class="guest-btn" type="button" id="guestBtn">Continue as Guest</button>
    
    <!-- Terms & Conditions -->
    <p class="p" style="font-size: 12px; color: #666; margin-top: 15px;">
      By signing in, you agree to our 
      <span class="span" id="openTerms">Terms & Conditions</span> and 
      <span class="span" id="openPrivacy">Privacy Policy</span>.
    </p>
  </form>
  
  <!-- Modal for Terms and Conditions / Privacy Policy -->
  <div class="modal" id="modalTerms">
    <div class="modal-content">
      <span class="close-modal" id="closeModal">&times;</span>
      <h2 id="modalTitle">Terms & Conditions</h2>
      <div class="terms-text">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent vehicula tincidunt ligula, ut sollicitudin urna porta nec. 
        Nulla facilisi. Vivamus ultrices, mi ut vestibulum dignissim, metus ex pellentesque urna, nec facilisis metus enim ut nisl. 
        Curabitur non urna a lorem faucibus ultrices. Donec vel enim sit amet nibh mollis gravida. Nulla blandit neque vitae ex 
        malesuada, non laoreet urna sollicitudin.</p>
        <p>Sed eget ante sed justo feugiat tincidunt. Fusce at erat at dui tempus accumsan. Integer vel commodo erat. Donec eu 
        erat eu urna tristique interdum. Curabitur tincidunt sem at felis efficitur, in elementum nibh placerat.</p>
      </div>
    </div>
  </div>
  
  <!-- Modal for Guest Details -->
  <div class="modal" id="guestModal">
    <div class="modal-content">
      <span class="close-modal" id="closeGuestModal">&times;</span>
      <h2>Guest Details</h2>
      <form id="guestForm">
        <div class="guest-field">
          <label for="guestName">Name</label>
          <input type="text" id="guestName" placeholder="Enter your Name" required>
        </div>
        <div class="guest-field">
          <label for="guestAge">Age</label>
          <input type="number" id="guestAge" placeholder="Enter your Age" required>
        </div>
        <button type="submit" class="button-submit" style="margin-top: 20px;">Submit</button>
      </form>
    </div>
  </div>
  
  <!-- JavaScript for functionalities -->
  <script>
    // Form submission (simulate sign-in)
    document.getElementById('loginForm').addEventListener('submit', function(e) {
      e.preventDefault();
      alert('Sign In functionality is not implemented yet.');
    });
    
    // Toggle password visibility
    const togglePassword = document.getElementById('togglePassword');
    const passwordInput = document.getElementById('password');
    togglePassword.addEventListener('click', function() {
      const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
      passwordInput.setAttribute('type', type);
    });
    
    // Social login redirects (demo)
    document.getElementById('googleLogin').addEventListener('click', function() {
      window.location.href = 'https://accounts.google.com/signin';
    });
    document.getElementById('appleLogin').addEventListener('click', function() {
      window.location.href = 'https://appleid.apple.com/auth/authorize';
    });
    
    // Continue as Guest: Open Guest Modal
    document.getElementById('guestBtn').addEventListener('click', function() {
      document.getElementById('guestModal').style.display = "flex";
    });
    
    // Forgot password and Sign Up (demo)
    document.getElementById('forgotPassword').addEventListener('click', function() {
      alert('Forgot password functionality is not implemented yet.');
    });
    document.getElementById('signUp').addEventListener('click', function() {
      alert('Sign Up functionality is not implemented yet.');
    });
    
    // Modal functionality for Terms & Privacy
    const modal = document.getElementById('modalTerms');
    const modalTitle = document.getElementById('modalTitle');
    const openTerms = document.getElementById('openTerms');
    const openPrivacy = document.getElementById('openPrivacy');
    const closeModal = document.getElementById('closeModal');
    
    openTerms.addEventListener('click', function() {
      modalTitle.textContent = "Terms & Conditions";
      modal.style.display = "flex";
    });
    openPrivacy.addEventListener('click', function() {
      modalTitle.textContent = "Privacy Policy";
      modal.style.display = "flex";
    });
    closeModal.addEventListener('click', function() {
      modal.style.display = "none";
    });
    window.addEventListener('click', function(e) {
      if (e.target === modal) {
        modal.style.display = "none";
      }
    });
    
    // Guest Modal functionality
    const guestModal = document.getElementById('guestModal');
    const closeGuestModal = document.getElementById('closeGuestModal');
    closeGuestModal.addEventListener('click', function() {
      guestModal.style.display = "none";
    });
    window.addEventListener('click', function(e) {
      if (e.target === guestModal) {
        guestModal.style.display = "none";
      }
    });
    // Handle guest form submission (demo)
    document.getElementById('guestForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = document.getElementById('guestName').value;
      const age = document.getElementById('guestAge').value;
      alert(`Guest Info Submitted\nName: ${name}\nAge: ${age}`);
      guestModal.style.display = "none";
    });
  </script>
</body>
</html>
