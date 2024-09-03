<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kanmani</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            margin: 0;
            padding: 0;
            background-image: url('https://i.pinimg.com/564x/d7/bb/a5/d7bba5f9544f277e1f909004c4355927.jpg');
            background-size: cover;
            font-family: 'San Francisco', Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
        }

        h1 {
            font-size: 40px;
            margin-top: 20px;
            font-family: 'San Francisco', Arial, sans-serif;
        }

        .container {
            text-align: center;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            margin-top: 20px;
        }

        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
            background-color: white;
            border: 2px solid #ccc;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            z-index: 1;
            text-align: center;
            border-radius: 10px;
            max-width: 80%;
        }

        .question {
            margin-bottom: 20px;
        }

        .options {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
        }

        button {
            background-color: #007AFF;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        #gif {
            position: fixed;
            width: 50px;
            height: 50px;
            z-index: 2;
        }

        #video-container {
            display: none;
        }

        #love-message {
            display: none;
            font-size: 24px;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            color: red;
            background: rgba(255, 255, 255, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            z-index: 3;
            animation: crash 5s linear infinite;
        }

        @keyframes fall {
            0% {
                transform: translateY(-100vh) translateX(-100vw);
            }
            100% {
                transform: translateY(100vh) translateX(100vw);
            }
        }

        @keyframes crash {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
        }
    </style>
</head>
<body>
    <h1>Kanmani</h1>

    <div class="container">
        <button onclick="showPopup('popup1')">Pop the first question</button>
    </div>

    <div class="popup" id="popup1">
        <div class="question">Do you love me?</div>
        <div class="options">
            <button onclick="nextPopup('popup2')">Yes</button>
            <button onclick="hidePopup()">No</button>
        </div>
        <img src="https://media.tenor.com/bWUeVRqW9-IAAAAi/fast-cat-cat-excited.gif" alt="GIF" id="gif">
    </div>

    <div class="popup" id="popup2">
        <div class="question">Why are you so cute?</div>
        <div class="options">
            <button onclick="nextPopup('popup3')">Yes</button>
            <button onclick="hidePopup()">No</button>
        </div>
    </div>

    <div class="popup" id="popup3">
        <div class="question">Will you always be mine?</div>
        <div class="options">
            <button onclick="nextPopup('popup4')">Yes</button>
            <button onclick="hidePopup()">No</button>
        </div>
    </div>

    <div class="popup" id="popup4">
        <div class="question">I love you, and you can't stop me?</div>
        <div class="options">
            <button onclick="nextPopup('popup5')">Yes</button>
            <button onclick="hidePopup()">No</button>
        </div>
    </div>

    <div class="popup" id="popup5">
        <div class="question">Play this video:</div>
        <div id="video-container">
            <iframe width="100%" height="100%" src="https://www.youtube.com/embed/dQw4w9WgXcQ?feature=shared" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <button onclick="playVideo()">Play Video</button>
    </div>

    <div class="popup" id="popup6">
        <div class="question">I love you.</div>
        <div id="love-message">I love you.</div>
    </div>

    <script>
        function showPopup(popupId) {
            document.getElementById(popupId).style.display = 'block';
        }

        function hidePopup() {
            const popups = document.querySelectorAll('.popup');
            popups.forEach(popup => {
                popup.style.display = 'none';
            });
            document.getElementById('video-container').style.display = 'none';
            document.getElementById('love-message').style.display = 'none';
        }

        function nextPopup(nextPopupId) {
            hidePopup();
            document.getElementById(nextPopupId).style.display = 'block';
        }

        function playVideo() {
            hidePopup();
            document.getElementById('video-container').style.display = 'block';
            document.getElementById('love-message').style.display = 'block';
        }

        // Code for randomly appearing GIFs
        function getRandomPosition() {
            const x = Math.random() * (window.innerWidth - 50); // Subtract gif width
            const y = Math.random() * (window.innerHeight - 50); // Subtract gif height
            return { x, y };
        }

        setInterval(() => {
            const gif = document.getElementById('gif');
            const position = getRandomPosition();
            gif.style.transform = `translate(${position.x}px, ${position.y}px)`;
        }, 300); // Change the interval as needed
    </script>
</body>
</html>
