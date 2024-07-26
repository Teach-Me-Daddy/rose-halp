<script>
  let positionX = 0;
  let positionY = 0;
  let clickCount = 0; // button click counter
  const buttonWidth = 50; // button width
  const buttonHeight = 50; // button height

  let timerInterval;
  let elapsedTime = 0;
  let isTimerRunning = false;

  // Function to move the button to a random position on screen and start counting clicks
  function moveButton() {
    // Ensure button stays within view
    positionX = Math.random() * (window.innerWidth - buttonWidth - 5); // 20px margin
    positionY = Math.random() * (window.innerHeight - buttonHeight - 254 - 5); // 20px margin
    clickCount += 1; // Click counter
  }

  function formatTime(ms) {
    const totalSeconds = Math.floor(ms / 1000);
    const minutes = Math.floor(totalSeconds / 60);
    const seconds = totalSeconds % 60;
    return `${String(minutes).padStart(1, "0")}:${String(seconds).padStart(2, "0")}`;
  }

  function startTimer() {
    if (!isTimerRunning) {
      const startTime = Date.now() - elapsedTime;
      timerInterval = setInterval(() => {
        elapsedTime = Date.now() - startTime;
        document.getElementById("timer").innerText = formatTime(elapsedTime);
      }, 1000);
      isTimerRunning = true;
    }
  }

  function pauseTimer() {
    if (isTimerRunning) {
      clearInterval(timerInterval);
      isTimerRunning = false;
    }
  }

  function resetTimer() {
    clearInterval(timerInterval);
    elapsedTime = 0;
    document.getElementById("timer").innerText = formatTime(elapsedTime);
    isTimerRunning = false;
  }
</script>

<!-- hell yeah tailwind-->
<div class="glass-container bg-white bg-opacity-20 backdrop-blur-lg rounded-xl p-6 mt-6 m-4">
  <!-- Title -->
  <p class="text-2xl font-bold text-center text-yellow-100">Find the button!</p>
  <!-- Display click count -->
  <p class="text-center text-lg text-white">Button clicked {clickCount} times</p>
  
  <!-- Timer display -->
  <div class="text-center text-lg text-white mb-4">
    Timer: <span id="timer">0:00</span>
  </div>

  <!-- Timer control buttons -->
  <div class="flex justify-center mb-4">
    <button
      class="bg-green-400 hover:bg-green-500 text-white font-bold py-2 px-4 rounded-full mr-2"
      on:click={startTimer}>Start</button>
    <button
      class="bg-yellow-400 hover:bg-yellow-500 text-white font-bold py-2 px-4 rounded-full mr-2"
      on:click={pauseTimer}>Pause</button>
    <button
      class="bg-red-400 hover:bg-red-500 text-white font-bold py-2 px-4 rounded-full"
      on:click={resetTimer}>Reset</button>
  </div>
</div>

<button
  class="bg-pink-400 hover:bg-pink-500 text-white font-bold rounded-full flex items-center justify-center text-sm"
  style="width: {buttonWidth}px; height: {buttonHeight}px; transform: translate({positionX}px, {positionY}px); position: absolute;"
  on:click={moveButton}
>
  Click Me
</button>

<!-- pastel rainbow gradient background animation. i dunno, it's pretty and gay-->
<style>
  :global(body) {
    background: linear-gradient(
      to right,
      #f3c1d1,
      #f4e8b5,
      #d1f4c6,
      #b5d6f4,
      #f4b5f7
    );
    background-size: 400% 400%;
    animation: gaydient 15s ease infinite;
  }

  @keyframes gaydient {
    0% {
      background-position: 0% 0%;
    }
    50% {
      background-position: 100% 100%;
    }
    100% {
      background-position: 0% 0%;
    }
  }

  .glass-container {
    max-width: 400px;
    margin: 20px auto;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    border-radius: 12px;
    padding: 20px;
    text-align: center;
  }

  button {
    padding: 10px 20px;
    border: none;
    border-radius: 25px;
    font-weight: bold;
    color: white;
    cursor: pointer;
    margin: 5px;
  }

  #move-button {
    position: absolute;
    background-color: #ff69b4;
  }

  .start-button {
    background-color: #28a745;
  }

  .pause-button {
    background-color: #ffc107;
  }

  .reset-button {
    background-color: #dc3545;
  }

  .title {
    font-size: 24px;
    font-weight: bold;
    color: #ffd700;
  }

  .counter, .timer {
    font-size: 18px;
    color: white;
  }
</style>
