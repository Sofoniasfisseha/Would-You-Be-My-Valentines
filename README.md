<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap">
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            overflow: hidden; /* Hide overflow for the img tag */
            background: url('https://saechaocirculation.files.wordpress.com/2017/04/look-as-it-falls.gif?w=900') fixed;
            background-size: cover;
            font-family: 'Great Vibes', cursive; /* Classy vintage style font */
        }
 #question {
            font-family: 'Great Vibes', cursive; /* Classy vintage style font */
            font-size: 72px; /* Doubled the size */
            text-align: center;
            margin-bottom: 20px;
            color: #fff; /* White text color */
            text-shadow: 0 0 10px #ff4d4d, 0 0 20px #ff4d4d, 0 0 30px #ff4d4d, 0 0 40px #ff0066, 0 0 70px #ff0066, 0 0 80px #ff0066, 0 0 100px #ff0066; /* Neon text effect */
        }
 #buttons {
            display: flex;
            justify-content: space-between;
            width: 150px; /* Adjusted width to half its previous size */
        }
    button {
            position: relative;
            overflow: hidden;
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 50px; /* Increased border-radius to make it more cloud-shaped */
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1;
            color: #fff; /* Text color for the buttons */
            background: linear-gradient(to right, #ff0066, #ff4d4d); /* Neon background gradient */
            border: 2px solid #ff4d4d; /* Red neon outline */
            text-shadow: 0 0 10px #ff4d4d, 0 0 20px #ff4d4d, 0 0 30px #ff4d4d; /* Neon text effect */
            font-family: 'Arial', sans-serif; /* Simplistic text font */
            font-weight: bold; /* Bold font */
        }
      button span {
            z-index: 2;
        }
    .cloud {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            clip-path: ellipse(80% 70% at 50% 50%);
            z-index: 0;
        }
  .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            align-items: center;
            justify-content: center;
            z-index: 2;
        }
.modal-content {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            position: relative;
        }
 .gif-container {
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
        }
      .gif-container img {
            max-width: 100%;
            max-height: 100%;
            border-radius: 5px;
        }
 .yey-message {
            font-family: 'Great Vibes', cursive; /* Classy vintage style font */
            color: #ff4d4d; /* Red neon color for the message */
            padding: 10px;
            border-radius: 5px;
            font-size: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
        }
 .heart-button {
            font-size: 24px;
            cursor: pointer;
            margin-left: 10px;
        }
 .bottom-left-text {
            font-family: 'Great Vibes', cursive; /* Classy vintage style font */
            font-style: italic; /* Italic style */
            position: fixed;
            bottom: 10px;
            left: 10px;
            font-size: 14px;
            animation: strobeColor 0.5s infinite alternate; /* Strobe and color change effect */
        }
@keyframes strobeColor {
            0%, 100% {
                color: #ff4d4d; /* Neon red color */
            }
            50% {
                color: #fff; /* White color */
            }
        }
  .hearts-container {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 3;
        }
  .heart {
            font-family: 'Great Vibes', cursive; /* Classy vintage style font */
            font-size: 20px;
            opacity: 0;
            animation: popOut 1s linear forwards, floatUp 5s linear infinite, flutter 0.5s infinite alternate, fadeOut 2.5s linear forwards;
            position: absolute;
        }
      @keyframes popOut {
            0% {
                transform: scale(0);
            }
            100% {
                transform: scale(1);
            }
        }
   @keyframes floatUp {
            0% {
                opacity: 1;
                transform: translateY(100vh) translateX(calc(-50% + 25px));
            }
            100% {
                opacity: 0;
                transform: translateY(-100vh) translateX(calc(-50% + 25px));
            }
        }
 @keyframes flutter {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }
   @keyframes fadeOut {
            0%, 100% {
                opacity: 1;
            }
            100% {
                opacity: 0;
            }
        }
 .show {
            display: flex;
        }
    </style>
</head>
<body>

  <div id="question">
        Would you be my <span style="font-weight: bold;">valentine</span> on the <span style="text-decoration: underline;">14.02.2024</span>?
    </div>

   <div id="buttons">
        <button onclick="showModal()">
            <div class="cloud"></div>
            <span style="font-weight: bold;">Yes</span>
        </button>
        <button onclick="moveButton()">
            <div class="cloud"></div>
            <span style="font-weight: bold;">No</span>
        </button>
    </div>

  <div class="modal" id="modal">
        <div class="modal-content">
            <div class="gif-container" id="gifContainer">
                <img src="https://i.imgflip.com/40047a.gif" alt="Pop-out Gif">
            </div>
            <div class="yey-message" id="yeyMessage">
                Yey! <span class="heart-button" onclick="showAppreciation()">💌</span>
            </div>
        </div>
    </div>

   <div class="bottom-left-text">
        Created by yours truly... Jimmy
    </div>

   <div class="hearts-container" id="heartsContainer"></div>

   <script>
        function showModal() {
            var modal = document.getElementById('modal');
            var yeyMessage = document.getElementById('yeyMessage');
            var heartsContainer = document.getElementById('heartsContainer');

            modal.classList.add('show');
            yeyMessage.style.display = 'flex';

            // Generate hearts and append them to the container
            for (var i = 0; i < 50; i++) {
                createHeart(heartsContainer, i);
            }

            setTimeout(function() {
                modal.classList.remove('show');
                yeyMessage.style.display = 'none';

                // Clear hearts after the animation
                heartsContainer.innerHTML = '';
            }, 15000); // Adjust the time to 15 seconds (15000 milliseconds = 15 seconds)
        }

        function moveButton() {
            var button = document.querySelector('button:last-child');

            var maxX = window.innerWidth - button.clientWidth;
            var maxY = window.innerHeight - button.clientHeight;

            var randomX = Math.floor(Math.random() * maxX);
            var randomY = Math.floor(Math.random() * maxY);

            button.style.position = 'absolute';
            button.style.left = randomX + 'px';
            button.style.top = randomY + 'px';
        }

        function createHeart(container, index) {
           var heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            container.appendChild(heart);
            var x = Math.random() * window.innerWidth;
            var y = Math.random() * window.innerHeight;
            heart.style.left = x + 'px'; // Random horizontal position
            heart.style.top = y + 'px'; // Random vertical position
            heart.style.animationDelay = '-' + Math.random() * 5 + 's'; // Random animation delay
            heart.style.setProperty('--index', index); // Set a CSS variable to the heart's index
        }

        function showAppreciation() {
            alert('I appreciate everything you have done for me in 2023, and I will forever and always do my best to show continuous love and support, my little snuggle bunny.');
        }
    </script>

</body>
</html>
