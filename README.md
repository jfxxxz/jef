<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JEF Profile</title>
    <style>
        /* Reset and base styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            background-color: #0a0a0a;
            color: #ffffff;
            overflow: hidden;
            height: 100vh;
            width: 100vw;
        }
        
        /* Entry screen */
        #entry-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #0a0a0a;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            cursor: pointer;
            transition: opacity 1s ease-in-out;
        }
        
        .entry-text {
            font-size: 1.5rem;
            font-weight: 300;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: #fbbf24;
        }
        
        /* Main content */
        .container {
            position: relative;
            width: 100%;
            height: 100vh;
            overflow: hidden;
        }
        
        /* Background image */
        .background-image {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: 1;
            /* Reduced blur from 8px to 3px for subtler effect */
            filter: blur(3px);
        }
        
        /* Yellowish overlay with transparency */
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* Enhanced golden yellowish hue with stronger color saturation and reduced backdrop blur */
            background: linear-gradient(
                to bottom,
                rgba(251, 191, 36, 0.45) 0%,
                rgba(245, 158, 11, 0.4) 30%,
                rgba(217, 119, 6, 0.35) 60%,
                rgba(180, 83, 9, 0.2) 100%
            );
            backdrop-filter: blur(2px);
            z-index: 2;
        }
        
        /* Content */
        .content {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            padding: 2rem;
            text-align: center;
        }
        
        /* Profile section */
        .profile {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1.5rem;
            max-width: 500px;
        }
        
        .profile-image-container {
            position: relative;
            width: 160px;
            height: 160px;
            border-radius: 50%;
            overflow: hidden;
            border: 4px solid rgba(251, 191, 36, 0.5);
            box-shadow: 0 0 40px rgba(251, 191, 36, 0.4);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .profile-image-container:hover {
            transform: scale(1.05);
            box-shadow: 0 0 60px rgba(251, 191, 36, 0.6);
        }
        
        .profile-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .name {
            font-size: 3.5rem; /* Increased font size from 2rem to 3.5rem for more prominence */
            font-weight: 600;
            color: #fbbf24;
            letter-spacing: 0.1em;
            text-shadow: 0 2px 15px rgba(251, 191, 36, 0.6);
            text-transform: uppercase;
        }
        
        .welcome-text {
            font-size: 1.25rem;
            font-weight: 300;
            letter-spacing: 0.15em;
            color: #fbbf24;
            text-transform: uppercase;
            text-shadow: 0 2px 10px rgba(251, 191, 36, 0.5);
        }
        
        .username {
            font-size: 3rem;
            font-weight: 700;
            color: #ffffff;
            text-shadow: 0 4px 20px rgba(0, 0, 0, 0.8);
            letter-spacing: 0.05em;
        }
        
        .tagline {
            font-size: 1.5rem;
            font-weight: 300;
            font-style: italic;
            letter-spacing: 0.1em;
            color: #fbbf24;
            text-shadow: 0 2px 10px rgba(251, 191, 36, 0.5);
        }
        
        /* Added social media links styling */
        .social-links {
            display: flex;
            gap: 1.5rem;
            margin-top: 2rem;
        }
        
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(251, 191, 36, 0.1);
            border: 2px solid rgba(251, 191, 36, 0.5);
            color: #fbbf24;
            text-decoration: none;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
        
        .social-link:hover {
            background: rgba(251, 191, 36, 0.3);
            border-color: #fbbf24;
            box-shadow: 0 0 20px rgba(251, 191, 36, 0.5);
            transform: translateY(-3px);
        }
        
        .social-link svg {
            width: 24px;
            height: 24px;
            fill: currentColor;
        }
        
        /* Added audio controls styling */
        .audio-controls {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            display: flex;
            align-items: center;
            gap: 1rem;
            z-index: 100;
        }
        
        .audio-button {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(251, 191, 36, 0.2);
            border: 2px solid rgba(251, 191, 36, 0.5);
            color: #fbbf24;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
        
        .audio-button:hover {
            background: rgba(251, 191, 36, 0.4);
            border-color: #fbbf24;
            box-shadow: 0 0 20px rgba(251, 191, 36, 0.5);
            transform: scale(1.05);
        }
        
        .audio-button svg {
            width: 24px;
            height: 24px;
            fill: currentColor;
        }
        
        .volume-control {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            background: rgba(251, 191, 36, 0.2);
            border: 2px solid rgba(251, 191, 36, 0.5);
            border-radius: 25px;
            padding: 0.75rem 1.25rem;
            backdrop-filter: blur(10px);
            opacity: 0;
            transform: translateX(20px);
            transition: all 0.3s ease;
            pointer-events: none;
        }
        
        .volume-control.active {
            opacity: 1;
            transform: translateX(0);
            pointer-events: all;
        }
        
        .volume-slider {
            width: 120px;
            height: 6px;
            border-radius: 3px;
            background: rgba(251, 191, 36, 0.3);
            outline: none;
            -webkit-appearance: none;
            appearance: none;
            cursor: pointer;
        }
        
        .volume-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #fbbf24;
            cursor: pointer;
            box-shadow: 0 0 10px rgba(251, 191, 36, 0.5);
            transition: all 0.2s ease;
        }
        
        .volume-slider::-webkit-slider-thumb:hover {
            transform: scale(1.2);
            box-shadow: 0 0 15px rgba(251, 191, 36, 0.8);
        }
        
        .volume-slider::-moz-range-thumb {
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #fbbf24;
            cursor: pointer;
            border: none;
            box-shadow: 0 0 10px rgba(251, 191, 36, 0.5);
            transition: all 0.2s ease;
        }
        
        .volume-slider::-moz-range-thumb:hover {
            transform: scale(1.2);
            box-shadow: 0 0 15px rgba(251, 191, 36, 0.8);
        }
        
        .volume-percentage {
            font-size: 0.875rem;
            font-weight: 600;
            color: #fbbf24;
            min-width: 40px;
            text-align: center;
        }
        
        @media (max-width: 768px) {
            .profile-image-container {
                width: 120px;
                height: 120px;
            }
            
            .name {
                font-size: 2.5rem; /* Increased mobile font size from 1.5rem to 2.5rem */
            }
            
            .username {
                font-size: 2rem;
            }
            
            .tagline {
                font-size: 1.125rem;
            }
            
            .welcome-text {
                font-size: 1rem;
            }
            
            .social-links {
                gap: 1rem;
                margin-top: 1.5rem;
            }
            
            .social-link {
                width: 45px;
                height: 45px;
            }
            
            .social-link svg {
                width: 20px;
                height: 20px;
            }
            
            .audio-controls {
                bottom: 1rem;
                right: 1rem;
                flex-direction: column;
                align-items: flex-end;
            }
            
            .volume-control {
                flex-direction: column;
                padding: 1rem;
            }
            
            .volume-slider {
                width: 100px;
            }
        }
        
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .fade-in {
            animation: fadeIn 1s ease-out forwards;
        }
        
        .animate-float {
            animation: float 3s ease-in-out infinite;
        }
    </style>
</head>
<body>
    <!-- Entry Screen -->
    <div id="entry-screen">
        <div class="entry-text">Enter</div>
    </div>
    
    <!-- Main Container -->
    <div class="container">
        <!-- Background Image -->
        <img src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/jujutsu-kaisen-season-2-episode-4-gojo-1024x576-WVKCvd5tOk9VQvBY6CN1xMNJuK61E9.jpeg" alt="Background" class="background-image">
        
        <!-- Yellowish Overlay -->
        <div class="overlay"></div>
        
        <!-- Content -->
        <div class="content">
            <div class="profile fade-in">
                <!-- Profile Image -->
                <div class="profile-image-container animate-float">
                    <img src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/ab67616d00001e0225c4fec3e7c3bca70335f33d%20%281%29-tS649i4EkOu6TgBYWuivTKD9ZssdZi.jpeg" alt="Satoru Gojo" class="profile-image">
                </div>
                
                <h2 class="name">JEF</h2>
                
                <!-- Welcome Text -->
                <p class="welcome-text">Welcome</p>
                
                <!-- Tagline -->
                <p class="tagline">The Strongest Sorcerer</p>
                
                <!-- Added social media links for Discord and TikTok -->
                <div class="social-links">
                    <a href="https://pt.quizur.com/trivia/voce-sabe-sobre-o-alisa-meu-pelo-TbZ6" target="_blank" rel="noopener noreferrer" class="social-link" aria-label="Discord">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                            <path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515a.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0a12.64 12.64 0 0 0-.617-1.25a.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057a19.9 19.9 0 0 0 5.993 3.03a.078.078 0 0 0 .084-.028a14.09 14.09 0 0 0 1.226-1.994a.076.076 0 0 0-.041-.106a13.107 13.107 0 0 1-1.872-.892a.077.077 0 0 1-.008-.128a10.2 10.2 0 0 0 .372-.292a.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127a12.299 12.299 0 0 1-1.873.892a.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028a19.839 19.839 0 0 0 6.002-3.03a.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419c0-1.333.956-2.419 2.157-2.419c1.21 0 2.176 1.096 2.157 2.42c0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419c0-1.333.955-2.419 2.157-2.419c1.21 0 2.176 1.096 2.157 2.42c0 1.333-.946 2.418-2.157 2.418z"/>
                        </svg>
                    </a>
                    <a href="https://www.tiktok.com/@y.jefersonxz?_r=1&_t=ZM-910ugErHuAt" target="_blank" rel="noopener noreferrer" class="social-link" aria-label="TikTok">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                            <path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74a2.89 2.89 0 0 1 2.31-4.64a2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 20.1a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.1z"/>
                        </svg>
                    </a>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Added audio element and controls -->
    <audio id="background-audio" loop>
        <source src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/THE%20HONORED%20ONE%20_%20Jujutsu%20Kaisen%20-%204K-JntgoVetkl2W4eRwQEEVXj9jsgR8GN.mp3" type="audio/mpeg">
    </audio>
    
    <div class="audio-controls">
        <div class="volume-control" id="volume-control">
            <input type="range" min="0" max="100" value="50" class="volume-slider" id="volume-slider">
            <span class="volume-percentage" id="volume-percentage">50%</span>
        </div>
        <button class="audio-button" id="audio-toggle" aria-label="Toggle audio">
            <svg id="play-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="M8 5v14l11-7z"/>
            </svg>
            <svg id="pause-icon" style="display: none;" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="M6 4h4v16H6V4zm8 0h4v16h-4V4z"/>
            </svg>
        </button>
    </div>
    
    <script>
        // Entry screen functionality
        const entryScreen = document.getElementById('entry-screen');
        
        // Handle entry screen click
        entryScreen.addEventListener('click', () => {
            entryScreen.style.opacity = '0';
            setTimeout(() => {
                entryScreen.style.display = 'none';
                // Auto-start music
                audio.play();
                playIcon.style.display = 'none';
                pauseIcon.style.display = 'block';
                volumeControl.classList.add('active');
                isPlaying = true;
            }, 1000);
        });
        
        // Optional: Auto-hide entry screen after 3 seconds
        setTimeout(() => {
            if (entryScreen.style.display !== 'none') {
                entryScreen.style.opacity = '0';
                setTimeout(() => {
                    entryScreen.style.display = 'none';
                    // Auto-start music
                    audio.play();
                    playIcon.style.display = 'none';
                    pauseIcon.style.display = 'block';
                    volumeControl.classList.add('active');
                    isPlaying = true;
                }, 1000);
            }
        }, 3000);
        
        const audio = document.getElementById('background-audio');
        const audioToggle = document.getElementById('audio-toggle');
        const playIcon = document.getElementById('play-icon');
        const pauseIcon = document.getElementById('pause-icon');
        const volumeControl = document.getElementById('volume-control');
        const volumeSlider = document.getElementById('volume-slider');
        const volumePercentage = document.getElementById('volume-percentage');
        
        let isPlaying = false;
        
        // Set initial volume
        audio.volume = 0.5;
        
        // Toggle audio play/pause
        audioToggle.addEventListener('click', () => {
            if (isPlaying) {
                audio.pause();
                playIcon.style.display = 'block';
                pauseIcon.style.display = 'none';
                volumeControl.classList.remove('active');
            } else {
                audio.play();
                playIcon.style.display = 'none';
                pauseIcon.style.display = 'block';
                volumeControl.classList.add('active');
            }
            isPlaying = !isPlaying;
        });
        
        // Volume control
        volumeSlider.addEventListener('input', (e) => {
            const volume = e.target.value / 100;
            audio.volume = volume;
            volumePercentage.textContent = `${e.target.value}%`;
        });
    </script>
</body>
</html>
