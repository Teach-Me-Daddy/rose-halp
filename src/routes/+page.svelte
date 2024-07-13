<script>
    let positionX = 0;
    let positionY = 0;
  
    // Function to move the button to a random position on screen
    function moveButton() {
      positionX = Math.random() * (window.innerWidth - 100); // Adjust for button width
      positionY = Math.random() * (window.innerHeight - 50); // Adjust for button height
    }
  </script>
  
  <!-- Tailwind CSS for styling - r u proud?? -->
  <div class="mb-4">
<!-- Title -->
    <p>Find the clit!</p>
  </div>
  
  <!-- button moving randomly using inline styles -->
  <button class="bg-pink-500 hover:bg-pink-700 text-white font-bold py-2 px-4 rounded-full flex items-center justify-center text-sm"
    style="width: 50px; height: 50px; /* adjust size as needed */
           transform: translate({positionX}px, {positionY}px); position: absolute;"
    on:click={moveButton}>
    Click Me
  </button>
  
  <style>
    /* dunno what i am doing */
  </style>
  