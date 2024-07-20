<script>
  let positionX = 0;
  let positionY = 0;
  let clickCount = 0; // button click counter
  const buttonWidth = 50; // button width
  const buttonHeight = 50; // button height

  // Function to move the button to a random position on screen and start counting clicks
  function moveButton() {
    // Ensure button stays within view
    positionX = Math.random() * (window.innerWidth - buttonWidth);
    positionY = Math.random() * (window.innerHeight - buttonHeight);
    clickCount += 1; // Click counter
  }
</script>

<!-- hell yeah tailwind-->
<div class="mb-4">
  <!-- title -->
  <p class="text-2xl font-bold text-center text-yellow-100">Find the button!</p>
  <p class="text-center text-lg text-white">Button clicked {clickCount} times</p> <!-- Display click count -->
</div>

<button
  class="bg-pink-400 hover:bg-pink-700 text-white font-bold rounded-full flex items-center justify-center text-sm"
  style="width: {buttonWidth}px; height: {buttonHeight}px; transform: translate({positionX}px, {positionY}px); position: absolute;"
  on:click={moveButton} 
>
  Click Me
</button>

<!-- pastel rainbow gradient background animation. i dunno, it's pretty and gay-->
<style>
  :global(body) {
    background: linear-gradient(to right, #f3c1d1, #f4e8b5, #d1f4c6, #b5d6f4, #f4b5f7);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;
  }

  @keyframes gaydient {
    0% { background-position: 0% 0%; }
    50% { background-position: 100% 100%; }
    100% { background-position: 0% 0%; }
  }
</style>
