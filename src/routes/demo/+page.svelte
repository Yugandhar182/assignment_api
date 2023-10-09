<script>
    import { onMount } from 'svelte';
  
    // Function to initialize the Google Sign-In API
    function initGoogleSignIn() {
      gapi.load('auth2', function() {
        gapi.auth2.init({
          client_id: '1028403675534-gsnclco2a306pcfbvo3264c74im3bksg.apps.googleusercontent.com', // Replace with your Google API client ID
        });
      });
    }
  
    // Function to handle the sign-in button click event
    function handleSignIn() {
      const auth2 = gapi.auth2.getAuthInstance();
      auth2.signIn().then(function(googleUser) {
        // Handle the user data after successful sign-in
        console.log('User signed in:', googleUser);
        // You can access user information using googleUser.getBasicProfile() and more
      });
    }
  
    onMount(() => {
      // Initialize Google Sign-In when the API script has loaded
      const script = document.createElement('script');
      script.src = 'https://apis.google.com/js/platform.js';
      script.onload = initGoogleSignIn;
      document.head.appendChild(script);
    });
  </script>
  
  <div>
    <button on:click={handleSignIn}>Sign in with Google</button>
  </div>
  