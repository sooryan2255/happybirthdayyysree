﻿<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Birthday Surprise for Sree! 🎉</title>
    <style>
        /* General Styles */
        body {
            margin: 0;
            padding: 0;
            font-family: 'Comic Sans MS', 'Comic Neue', cursive, sans-serif;
            background: linear-gradient(to right, #ffe6f7, #ffe0ec);
            text-align: center;
            overflow-x: hidden;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        /* Floating Hearts Background */
        .heart-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; /* Crucial: ensures hearts don't block clicks */
            overflow: hidden; /* Hide hearts outside the view */
            z-index: -1; /* Place hearts behind other content */
        }

        .heart {
            position: absolute;
            background-color: rgba(255, 192, 203, 0.7); /* Pink hearts */
            width: 15px;
            height: 15px;
            transform: rotate(-45deg); /* To make it heart-shaped */
            animation: floatHeart 10s infinite ease-in-out; /* Main animation */
        }

        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            background-color: rgba(255, 192, 203, 0.7);
        }

        .heart::before {
            top: -7.5px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: 7.5px;
        }

        /* Define the floating animation */
        @keyframes floatHeart {
            0% {
                transform: translateY(100vh) rotate(-45deg) scale(0.5);
                opacity: 0;
            }
            25% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-100px) rotate(-45deg) scale(1.5);
                opacity: 0;
            }
        }

        /* Stagger animation start times for variety */
        .heart:nth-child(1) { left: 10%; animation-delay: 0s; }
        .heart:nth-child(2) { left: 20%; animation-delay: 2s; background-color: rgba(255, 105, 180, 0.7); }
        .heart:nth-child(3) { left: 30%; animation-delay: 4s; }
        .heart:nth-child(4) { left: 40%; animation-delay: 6s; background-color: rgba(255, 105, 180, 0.7); }
        .heart:nth-child(5) { left: 50%; animation-delay: 8s; }
        .heart:nth-child(6) { left: 60%; animation-delay: 1s; background-color: rgba(255, 192, 203, 0.9); }
        .heart:nth-child(7) { left: 70%; animation-delay: 3s; }
        .heart:nth-child(8) { left: 80%; animation-delay: 5s; background-color: rgba(255, 192, 203, 0.9); }
        .heart:nth-child(9) { left: 90%; animation-delay: 7s; }
        .heart:nth-child(10) { left: 5%; animation-delay: 9s; }


        /* Step Styling (for smooth transitions) */
        .step {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0.9);
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.7s ease-out, transform 0.7s ease-out, visibility 0.7s ease-out;
            animation: fadeInScale 0.7s forwards; /* New: Add fade-in-scale animation for new steps */

            padding: 50px 20px;
            width: 90%;
            max-width: 600px;
            box-sizing: border-box;
            background-color: rgba(255, 255, 255, 0.9); /* Add a slight background to steps */
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
        }

        .active {
            opacity: 1;
            transform: translate(-50%, -50%) scale(1);
            visibility: visible;
            animation: none; /* Remove animation if it's already active */
        }

        /* Keyframes for the new step transition */
        @keyframes fadeInScale {
            0% {
                opacity: 0;
                transform: translate(-50%, -50%) scale(0.9);
            }
            100% {
                opacity: 1;
                transform: translate(-50%, -50%) scale(1);
            }
        }

        /* Mascot Styles */
        #mascot {
            position: fixed;
            bottom: 20px; /* Distance from the bottom */
            left: 20px;  /* Distance from the left */
            top: auto;   /* Remove top positioning */
            right: auto; /* Remove right positioning */

            display: flex;
            align-items: center;
            background-color: rgba(255, 255, 255, 0.85);
            border-radius: 20px;
            padding: 10px 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            z-index: 101; /* Higher than step's box-shadow */
            max-width: 300px;
            text-align: left;
            transform: translateY(150%); /* Start below screen */
            animation: slideInMascot 1s forwards; /* Slide in on load */
            border: 2px solid #ffccdd;
            transition: opacity 0.5s ease-out, transform 0.5s ease-out; /* Added transition for smooth fade/slide out */
        }

        #mascot.hidden { /* New class for hiding the mascot */
            opacity: 0;
            transform: translateY(150%); /* Slide it back down */
            pointer-events: none; /* Make it unclickable when hidden */
        }

        #mascot img {
            width: 60px;
            height: auto;
            margin-right: 10px;
            flex-shrink: 0;
        }

        #mascot-message {
            font-size: 0.95em;
            color: #6a0dad;
            font-weight: bold;
            line-height: 1.3;
        }

        /* Adjust animation for sliding up from bottom */
        @keyframes slideInMascot {
            to {
                transform: translateY(0);
            }
        }

        /* New: Welcome Step Specific Styles */
        #welcome-step h2 {
            font-size: 2.5em;
            color: #ff69b4;
            margin-bottom: 20px;
        }

        #welcome-step p {
            font-size: 1.2em;
            color: #6a0dad;
            margin-bottom: 30px;
            line-height: 1.5;
        }

        /* Balloon Game (Step 1) */
        .balloon-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 30px;
            margin-top: 40px;
        }

        .balloon {
            width: 90px;
            height: 120px;
            border-radius: 50% 50% 60% 60%;
            position: relative;
            cursor: pointer;
            box-shadow: inset -3px -3px 10px rgba(255,255,255,0.7), 0 10px 20px rgba(0,0,0,0.2);
            transition: transform 0.2s ease-out, background 0.2s ease-out, opacity 0.3s ease-out, width 0.3s ease-out, height 0.3s ease-out;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2em;
        }

        .balloon:hover {
            transform: translateY(-10px) scale(1.05);
        }

        .balloon.popped {
            animation: balloonPop 0.3s forwards;
            opacity: 0;
            pointer-events: none;
        }

        @keyframes balloonPop {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.8; }
            100% { transform: scale(0); opacity: 0; }
        }

        .balloon::after {
            content: '';
            position: absolute;
            width: 3px;
            height: 60px;
            background: #555;
            bottom: -60px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 0 0 50% 50%;
        }

        /* Drag and Drop (Step 2) */
        .drag-box {
            width: 180px;
            height: 180px;
            border: 4px dashed #ff69b4;
            margin: 40px auto;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #ff69b4;
            font-size: 1.5em;
            border-radius: 10px;
            transition: border-color 0.3s ease, background-color 0.3s ease, border-style 0.3s ease, border-width 0.3s ease;
        }

        .drag-box.drag-over {
            border-color: hotpink;
            border-style: solid;
            border-width: 6px;
            background-color: rgba(255, 105, 180, 0.1);
        }

        .gift {
            font-size: 4em;
            cursor: grab;
            transition: transform 0.2s ease-out, box-shadow 0.2s ease-out;
        }

        /* Wish Textarea (Step 3) */
        textarea {
            border: 2px solid #ff69b4;
            border-radius: 10px;
            padding: 15px;
            font-family: 'Comic Sans MS', cursive;
            font-size: 1.1em;
            resize: vertical;
            width: 80%;
            max-width: 400px;
            box-sizing: border-box;
            outline: none;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }

        textarea:focus {
            border-color: #ff1493;
            box-shadow: 0 0 10px rgba(255, 105, 180, 0.5);
        }

        /* Buttons */
        button {
            background-color: #ff69b4;
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 30px;
            font-family: 'Comic Sans MS', cursive;
            font-size: 1.1em;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(255, 105, 180, 0.4);
            transition: background-color 0.3s ease, transform 0.2s ease;
            margin-top: 20px;
        }

        button:hover {
            background-color: #ff1493;
            transform: translateY(-3px);
        }

        /* Candle Container for multiple candles */
        .candle-container {
            display: flex;
            justify-content: center;
            gap: 15px; /* Space between candles */
            margin-top: 80px;
            flex-wrap: wrap; /* Allow candles to wrap on smaller screens */
        }

        .candle {
            width: 40px; /* Slightly smaller candles */
            height: 80px;
            position: relative;
            border-radius: 10px;
            background: linear-gradient(to bottom, #ff95d5, #7873f5);
            box-shadow: 0 0 15px rgba(255, 105, 180, 0.5);
            cursor: pointer;
            transition: transform 0.2s ease;
        }

        .candle:hover {
            transform: translateY(-5px); /* Lift slightly on hover */
        }

        .flame {
            position: absolute;
            top: -30px; /* Adjust flame position */
            left: 50%;
            transform: translateX(-50%);
            width: 20px; /* Smaller initial flame */
            height: 30px;
            background: radial-gradient(circle, #fff 0%, #ff0 30%, #ffa500 70%, transparent 80%);
            border-radius: 50% 50% 50% 50%;
            opacity: 0; /* Initially invisible (unlit) */
            animation: none; /* No flicker initially */
            transition: opacity 0.3s ease-out, transform 0.3s ease-out, background 0.3s ease-out;
            transform-origin: bottom center;
        }

        .flame.lit-flame { /* New class for lit flames */
            opacity: 1;
            animation: flicker 0.3s infinite alternate; /* Flicker when lit */
        }

        @keyframes flicker {
            0% { transform: translateX(-50%) scale(1); }
            100% { transform: translateX(-50%) scale(1.1); }
        }

        /* Confetti Canvas - for the final step */
        #confetti-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9999;
        }

        /* Cursor Sparkle */
        .cursor-sparkle {
            position: absolute;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: radial-gradient(circle, #fff 0%, pink 60%, transparent 100%);
            pointer-events: none;
            animation: fadeOut 1s forwards;
            z-index: 100000;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                transform: scale(2.5);
            }
        }

        /* Final Letter (Final Step) */
        #final-letter {
            margin-top: 30px;
            font-family: 'Georgia', serif;
            font-size: 1.1em;
            color: #333;
            white-space: pre-wrap;
            border-top: 2px dashed #ff99cc;
            padding-top: 25px;
            max-width: 550px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.6;
            text-align: left;
        }

        .cake-img {
            max-width: 80%;
            height: auto;
            margin-top: 20px;
        }

        /* Final Message Popup Styles */
        #final-popup-message {
            position: fixed;
            bottom: 50%; /* Center vertically */
            left: 50%;
            transform: translate(-50%, 50%); /* Adjust to truly center */
            background-color: #fff;
            border: 3px solid #ff69b4;
            border-radius: 15px;
            padding: 25px 35px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            font-family: 'Comic Sans MS', cursive;
            font-size: 1.3em;
            color: #6a0dad;
            z-index: 1000; /* Ensure it's above other content */
            opacity: 0; /* Start invisible */
            transform: translate(-50%, 50%) scale(0.8); /* Start slightly smaller */
            transition: opacity 0.5s ease-out, transform 0.5s ease-out;
            pointer-events: none; /* Do not block clicks by default */
            text-align: center;
        }

        #final-popup-message.show {
            opacity: 1;
            transform: translate(-50%, 50%) scale(1);
            pointer-events: all; /* Allow clicks when shown */
        }

        /* Gift Box Styles */
        #gift-instruction { /* NEW: Instruction message for gifts */
            font-size: 1.1em;
            color: #6a0dad;
            margin-bottom: 20px;
            opacity: 0; /* Initially hidden */
            transform: translateY(10px);
            transition: opacity 0.7s ease-out, transform 0.7s ease-out;
        }

        #gift-instruction.show {
            opacity: 1;
            transform: translateY(0);
        }

        #gift-boxes-container {
            display: flex;
            justify-content: center;
            gap: 30px; /* Space between boxes */
            margin-top: 20px; /* Adjusted margin */
            opacity: 0; /* Initially hidden */
            transform: translateY(20px); /* Start slightly below */
            transition: opacity 0.7s ease-out, transform 0.7s ease-out;
            pointer-events: none; /* Do not block clicks when hidden */
        }

        #gift-boxes-container.show {
            opacity: 1;
            transform: translateY(0);
            pointer-events: all; /* Allow clicks when shown */
        }

        .gift-box {
            width: 120px;
            height: 120px;
            background-color: #ffc0cb; /* Light pink background for boxes */
            border: 3px solid #ff69b4;
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
            overflow: hidden; /* Hide overflowing content (photo) initially */
            position: relative; /* For absolute positioning of photo */
        }

        .gift-box:hover {
            transform: translateY(-5px) scale(1.03);
            background-color: #ffe0ec; /* Lighter on hover */
            box-shadow: 0 12px 25px rgba(0, 0, 0, 0.3);
        }

        .box-emoji {
            font-size: 3em;
            transition: opacity 0.3s ease;
        }

        .gift-box.opened .box-emoji {
            opacity: 0; /* Hide emoji when box is opened */
        }

        .gift-reveal-photo {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover; /* Cover the box area */
            opacity: 0; /* Initially hidden */
            transform: scale(0.8); /* Start slightly smaller */
            transition: opacity 0.5s ease-out, transform 0.5s ease-out;
        }

        .gift-box.opened .gift-reveal-photo {
            opacity: 1;
            transform: scale(1);
        }

    </style>
</head>
<body>
    <div class="heart-container">
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
        <div class="heart"></div>
    </div>

    <div id="mascot">
        <img src="https://www.citypng.com/public/uploads/preview/cute-cartoon-cat-transparent-background-735811696674569pfu81cnq1t.png" alt="Cute Cat Mascot">
        <p id="mascot-message"></p>
    </div>

    <div id="welcome-step" class="step active">
        <h2>🎉 Happy Birthday, Sree! 🎉</h2>
        <p>Get ready for a little surprise game I made just for you!</p>
        <button id="startGameButton">Let's Start the Fun! 😊</button>
    </div>

    <div id="step1" class="step">
        <h2>🎈 Tap the Right Balloon 🎈</h2>
        <p>Only one balloon will pop with glitter! Choose wisely...</p>
        <div class="balloon-container" id="balloonContainer"></div>
    </div>

    <div id="step2" class="step">
        <h2>🎁 Drag the Gift into the Box 🎁</h2>
        <p>Drag the gift below into the surprise box!</p>
        <div class="gift" id="gift" draggable="true">🎁</div>
        <div class="drag-box" id="dropBox">Drop Here</div>
    </div>

    <div id="step3" class="step">
        <h2>💌 Write a Birthday Wish 💌</h2>
        <p>Write something sweet below!</p>
        <textarea id="wishText" rows="4" cols="30" placeholder="Type your wish here..."></textarea><br>
        <button>Submit Wish</button>
    </div>

    <div id="step4" class="step">
        <h2>🎂 Light Up the Candles! 🎂</h2>
        <p id="candleInstructions">Click each flame to light up all the candles!</p>
        <div class="candle-container"> <div class="candle lightable-candle" data-lit="false">
                <div class="flame unlit-flame"></div>
            </div>
            <div class="candle lightable-candle" data-lit="false">
                <div class="flame unlit-flame"></div>
            </div>
            <div class="candle lightable-candle" data-lit="false">
                <div class="flame unlit-flame"></div>
            </div>
            <div class="candle lightable-candle" data-lit="false">
                <div class="flame unlit-flame"></div>
            </div>
            <div class="candle lightable-candle" data-lit="false">
                <div class="flame unlit-flame"></div>
            </div>
        </div>
    </div>

    <div id="final" class="step">
        <h1>🎀 HAPPY BIRTHDAY <span id="nameTarget">SREEEE</span> 🎀</h1>
        <p>“Forget the past; look forward to the future, for the best things are yet to come.”💝</p>
        <img class="cake-img" src="https://static.vecteezy.com/system/resources/previews/036/053/459/non_2x/ai-generated-cartoon-birthday-cake-transparent-background-free-png.png" alt="Birthday Cake">
        <div id="final-letter"></div>
        <canvas id="confetti-canvas"></canvas>

        <p id="gift-instruction" style="margin-top: 50px;">These are my gifts for you! Tap to open! 😊</p>

        <div id="gift-boxes-container">
            <div class="gift-box" id="giftBox1">
                <span class="box-emoji">🎁</span>
                <img src="https://www.fnp.com/images/pr/philippines/x/v20220223110123/ferrero-rocher-chocolate-box-8-pcs_1.jpg" alt="Chocolate Gift" class="gift-reveal-photo">
            </div>
            <div class="gift-box" id="giftBox2">
                <span class="box-emoji">🎁</span>
                <img src="https://clickcuisineuae.com/cdn/shop/products/Hershey-s-Kisses-Milk-Chocolate-100gm-Kisses-1667800620.jpg?v=1667800622&width=990" alt="Hershey's Kisses Gift" class="gift-reveal-photo">
            </div>
        </div>
    </div>

    <div id="final-popup-message">
        <p>I hope you like it! ❤️</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // --- DOM Element References ---
            const startGameButton = document.getElementById('startGameButton');
            const balloonContainer = document.getElementById("balloonContainer");
            const gift = document.getElementById("gift");
            const dropBox = document.getElementById("dropBox");
            const wishTextarea = document.getElementById("wishText");
            const submitWishButton = document.querySelector("#step3 button");
            const candleInstructions = document.getElementById("candleInstructions");
            const finalLetterTarget = document.getElementById('final-letter');
            const nameTarget = document.getElementById('nameTarget');
            const confettiCanvas = document.getElementById('confetti-canvas');
            const finalPopupMessage = document.getElementById('final-popup-message');
            const candleContainer = document.querySelector('.candle-container');
            const giftInstruction = document.getElementById('gift-instruction');
            const giftBoxesContainer = document.getElementById('gift-boxes-container');
            const giftBox1 = document.getElementById('giftBox1');
            const giftBox2 = document.getElementById('giftBox2');


            // Mascot References
            const mascot = document.getElementById('mascot');
            const mascotMessage = document.getElementById('mascot-message');

            let currentStep = 'welcome-step';
            let correctBalloonIndex;
            let litCandlesCount = 0;
            const totalCandles = 5;
            let openedGiftsCount = 0; // To track opened gifts
            let hintTimeout; // For mascot hints

            // --- Mascot Messages ---
            const mascotMessages = {
                'welcome-step': 'Hello Sree! I have a fun surprise game for you. Click the button to start!',
                'step1': 'Meow! Hey Sree, tap the right balloon to find the sparkle! You can do it!',
                'step1-hint': 'Psst! Sree, keep trying balloons! You\'re looking for the one with extra shimmer. Tap one by one!',
                'step2': 'Purr-fect! Now, Sree, drag that lovely gift into the box for your surprise!',
                'step2-hint': 'Woof! Sree, you need to drag the gift with your mouse or finger into the box. Make sure it lands inside!',
                'step3': 'Almost there, Sree! Write a super sweet birthday wish here. She\'ll adore it!',
                'step3-hint': 'Don\'t be shy, Sree! Just type a lovely message in the box. Even a short "Happy Birthday!" is wonderful!',
                'step4': 'Just one more step, Sree! Click each flame to light up all the candles!',
                'step4-hint': 'Sree, you need to tap on each candle\'s flame to light it up. Light them all to proceed!',
                'final': 'Paw-some! Happy Birthday, Sree! Enjoy your special message and all the confetti!'
            };

            // Function to update mascot's message
            function updateMascotMessage(stepId) {
                mascotMessage.innerText = mascotMessages[stepId];
                // Clear any existing hint timeout
                clearTimeout(hintTimeout);
                // Set a new hint timeout for game steps (if a hint exists for this step)
                if (mascotMessages[stepId + '-hint']) {
                    hintTimeout = setTimeout(() => {
                        mascotMessage.innerText = mascotMessages[stepId + '-hint'];
                    }, 10000); // Show hint after 10 seconds on the same step
                }
            }


            // --- Step Navigation Function ---
            function nextStep(showId) {
                document.getElementById(currentStep).classList.remove('active');
                
                const nextStepElement = document.getElementById(showId);
                if (nextStepElement) {
                    nextStepElement.classList.add('active');
                }
                
                currentStep = showId;
                updateMascotMessage(currentStep);

                if (currentStep === 'final') {
                    mascot.classList.add('hidden');
                } else {
                    mascot.classList.remove('hidden');
                }
            }

            // Event listener for the "Start Game" button
            startGameButton.addEventListener('click', () => {
                nextStep('step1'); // Move to the first game step
            });


            // --- Step 1: Balloon Pop Game ---
            const balloonColors = [
                'radial-gradient(circle at 30% 30%, #ff89c4, #ff1493)',
                'radial-gradient(circle at 30% 30%, #a4e5ee, #1e90ff)',
                'radial-gradient(circle at 30% 30%, #d4a7f0, #9370db)',
                'radial-gradient(circle at 30% 30%, #fff7a0, #ffd700)',
                'radial-gradient(circle at 30% 30%, #b3f7b3, #3cb371)'
            ];

            function setupBalloons() {
                correctBalloonIndex = Math.floor(Math.random() * 5);
                // Clear existing balloons if any (for replayability)
                balloonContainer.innerHTML = ''; 
                for (let i = 0; i < 5; i++) {
                    const balloon = document.createElement("div");
                    balloon.className = "balloon";
                    balloon.setAttribute('role', 'button');
                    balloon.setAttribute('aria-label', `Balloon ${i + 1}`);
                    balloon.style.background = balloonColors[i];

                    balloon.addEventListener('click', () => {
                        if (i === correctBalloonIndex) {
                            balloon.classList.add('popped');
                            balloon.style.background = 'radial-gradient(circle at 30% 30%, #ffd700, #ffa500)';
                            balloon.innerText = '✨';
                            setTimeout(() => {
                                balloon.remove(); 
                                nextStep('step2');
                            }, 500);
                        } else {
                            balloon.style.opacity = 0.3;
                            balloon.style.pointerEvents = 'none';
                        }
                    });
                    balloonContainer.appendChild(balloon);
                }
            }

            // --- Step 2: Drag and Drop Gift ---
            function setupDragAndDrop() {
                // Reset gift position and visibility (for replayability)
                gift.style.display = 'block';
                gift.style.transform = 'none';
                gift.style.boxShadow = 'none';
                dropBox.innerText = 'Drop Here';
                dropBox.style.backgroundColor = ''; // Reset background
                
                // Ensure event listeners are only added once or handle multiple assignments carefully
                // For simplicity, we'll assume initializeGame is called once at start or after full reset.
                gift.ondragstart = e => {
                    e.dataTransfer.setData("text/plain", e.target.id);
                    e.dataTransfer.effectAllowed = "move";
                    e.target.style.transform = 'scale(1.1) translateY(-5px)';
                    e.target.style.boxShadow = '0 15px 30px rgba(0,0,0,0.3)';
                };

                gift.ondragend = e => {
                    if (gift.style.display !== 'none') {
                        e.target.style.transform = 'none';
                        e.target.style.boxShadow = 'none';
                    }
                };

                dropBox.ondragover = e => {
                    e.preventDefault();
                    e.dataTransfer.dropEffect = "move";
                    dropBox.classList.add('drag-over');
                };

                dropBox.ondragleave = () => {
                    dropBox.classList.remove('drag-over');
                };

                dropBox.ondrop = e => {
                    e.preventDefault();
                    const data = e.dataTransfer.getData("text/plain");

                    if (data === "gift") {
                        dropBox.innerText = "🎉 Thank you!";
                        dropBox.style.backgroundColor = '#fff0f5';
                        gift.style.display = 'none';
                        setTimeout(() => { nextStep('step3'); }, 1000);
                    }
                    dropBox.classList.remove('drag-over');
                };
            }

            // --- Step 3: Birthday Wish ---
            submitWishButton.addEventListener('click', () => {
                const wishText = wishTextarea.value.trim();
                if (wishText.length > 0) {
                    nextStep('step4');
                } else {
                    alert("Please type your wish first!");
                    wishTextarea.focus();
                }
            });

            // --- Step 4: Light Up Candles ---
            if (candleContainer) {
                // Remove existing listener to prevent duplicates if initializeGame is called multiple times
                // This is a robust way to handle it for replayability
                const oldCandleListener = candleContainer._candleListener; // Store previous listener
                if (oldCandleListener) {
                    candleContainer.removeEventListener('click', oldCandleListener);
                }

                const newCandleListener = (event) => {
                    const clickedFlame = event.target.closest('.flame');
                    if (clickedFlame && !clickedFlame.classList.contains('lit-flame')) {
                        clickedFlame.classList.add('lit-flame');
                        litCandlesCount++;
                        candleInstructions.innerText = `Click ${totalCandles - litCandlesCount} more flame(s) to light all candles!`;

                        if (litCandlesCount === totalCandles) {
                            candleInstructions.innerText = "All candles are lit! Happy Birthday!";
                            setTimeout(() => {
                                nextStep('final');
                                setTimeout(() => {
                                    startTypingLetter();
                                    fireConfetti();
                                }, 1500);
                            }, 1000);
                        }
                    }
                };
                candleContainer.addEventListener('click', newCandleListener);
                candleContainer._candleListener = newCandleListener; // Store current listener
            }

            // --- Final Step Animations and Letter ---

            // Initialize canvas-confetti with the specific canvas element
            const myConfetti = confetti.create(confettiCanvas, { resize: true, useWorker: true });

            // Confetti Function using canvas-confetti
            function fireConfetti() {
                myConfetti({
                    particleCount: 150,
                    spread: 120,
                    origin: { y: 0.6, x: 0.5 },
                    colors: ['#FF69B4', '#FFD700', '#ADD8E6', '#9370DB', '#00CED1'],
                    shapes: ['square', 'circle'],
                    scalar: 1.2
                });

                setTimeout(() => {
                    myConfetti({
                        particleCount: 100,
                        spread: 120,
                        origin: { y: 0.7, x: 0.4 },
                        colors: ['#FF1493', '#FFFF00', '#87CEEB', '#BA55D3'],
                        shapes: ['star', 'circle'],
                        scalar: 1.0
                    });
                }, 200);

                setTimeout(() => {
                    myConfetti({
                        particleCount: 100,
                        spread: 120,
                        origin: { y: 0.7, x: 0.6 },
                        colors: ['#FFC0CB', '#FFEFD5', '#6A5ACD', '#40E0D0'],
                        shapes: ['circle', 'square'],
                        scalar: 0.9
                    });
                }, 400);
            }


            function startTypingLetter() {
                const letter = `Hey Sree,
Happy Birthday! 🎉✨
It’s kind of crazy how a random snap turned into this lovely friendship. I’m really glad we started talking — our daily chats always add a little something extra to my day.
You’re such a sweet and genuine person, and you truly deserve all the happiness in the world. Hope your day is as amazing as you are.
Enjoy every moment and keep smiling! 💛`;

                let i = 0;
                finalLetterTarget.innerText = ''; // Clear previous text for re-typing if replayed
                const speed = 40;
                const interval = setInterval(() => {
                    if (i < letter.length) {
                        finalLetterTarget.innerText += letter.charAt(i);
                        i++;
                    } else {
                        clearInterval(interval);
                        // Show gift instruction and boxes AFTER letter types
                        setTimeout(() => {
                            giftInstruction.classList.add('show');
                            giftBoxesContainer.classList.add('show');
                        }, 1000); // Wait 1 second after letter finishes
                    }
                }, speed);
            }

            // Event Listeners for Gift Boxes
            if (giftBox1) {
                const oldGiftBox1Listener = giftBox1._giftBoxListener;
                if (oldGiftBox1Listener) giftBox1.removeEventListener('click', oldGiftBox1Listener);
                const newGiftBox1Listener = () => {
                    if (!giftBox1.classList.contains('opened')) { // Prevent multiple opens
                        giftBox1.classList.add('opened');
                        openedGiftsCount++;
                        checkAllGiftsOpened();
                    }
                };
                giftBox1.addEventListener('click', newGiftBox1Listener);
                giftBox1._giftBoxListener = newGiftBox1Listener;
            }

            if (giftBox2) {
                const oldGiftBox2Listener = giftBox2._giftBoxListener;
                if (oldGiftBox2Listener) giftBox2.removeEventListener('click', oldGiftBox2Listener);
                const newGiftBox2Listener = () => {
                    if (!giftBox2.classList.contains('opened')) { // Prevent multiple opens
                        giftBox2.classList.add('opened');
                        openedGiftsCount++;
                        checkAllGiftsOpened();
                    }
                };
                giftBox2.addEventListener('click', newGiftBox2Listener);
                giftBox2._giftBoxListener = newGiftBox2Listener;
            }

            // Function to check if both gifts are opened
            function checkAllGiftsOpened() {
                if (openedGiftsCount === 2) {
                    // Show final popup message after an ADDITIONAL delay (3 seconds after gifts are fully opened)
                    setTimeout(() => {
                        finalPopupMessage.classList.add('show');
                    }, 3000); // 3 seconds after the second gift is opened
                }
            }


            // Cursor Sparkle Effect
            document.addEventListener('mousemove', e => {
                // Only show sparkle effect on the final step AND if the final popup isn't shown
                // AND if the gift boxes are not yet shown (so sparkles don't appear over them initially)
                if (!document.getElementById('final').classList.contains('active') || finalPopupMessage.classList.contains('show') || giftBoxesContainer.classList.contains('show')) return;

                const sparkle = document.createElement('div');
                sparkle.className = 'cursor-sparkle';
                sparkle.style.left = e.pageX + 'px';
                sparkle.style.top = e.pageY + 'px';
                document.body.appendChild(sparkle);

                sparkle.addEventListener('animationend', () => {
                    sparkle.remove();
                });
            });

            // --- Initialization ---
            function initializeGame() {
                // Ensure only the welcome step is active initially
                document.getElementById('welcome-step').classList.add('active');
                document.getElementById('step1').classList.remove('active');
                document.getElementById('step2').classList.remove('active');
                document.getElementById('step3').classList.remove('active');
                document.getElementById('step4').classList.remove('active');
                document.getElementById('final').classList.remove('active');

                // Reset game states
                openedGiftsCount = 0; // Reset for gifts
                litCandlesCount = 0; // Reset for candles

                // Clear existing balloons and set up new ones
                balloonContainer.innerHTML = ''; // Clear old balloons
                setupBalloons();
                
                // Setup drag and drop for gift
                setupDragAndDrop();

                // Reset candle state
                const allFlames = document.querySelectorAll('.flame');
                allFlames.forEach(flame => {
                    flame.classList.remove('lit-flame');
                    flame.classList.add('unlit-flame');
                });
                candleInstructions.innerText = `Click each flame to light up all the candles!`;

                // Reset wish textarea
                wishTextarea.value = '';

                // Ensure gift instruction, gift boxes and final popup are hidden on initialization
                giftInstruction.classList.remove('show');
                giftBoxesContainer.classList.remove('show');
                finalPopupMessage.classList.remove('show');
                
                // Ensure gift boxes are closed if replayed
                if (giftBox1) giftBox1.classList.remove('opened');
                if (giftBox2) giftBox2.classList.remove('opened');

                // Reset mascot message and clear any pending hints
                updateMascotMessage(currentStep);
                clearTimeout(hintTimeout);
            }

            initializeGame();
        });
    </script>
<audio autoplay loop>
  <source src="birthday.mp3" type="audio/mpeg">
</audio>

</body>
</html>
