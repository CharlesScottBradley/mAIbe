<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reveal inL</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #000;
            color: #fff;
            font-family: 'Arial', sans-serif;
        }
        #countdown {
            font-size: 5em;
        }
    </style>
</head>
<body>
    <div id="countdown"></div>

    <script>
        function updateCountdown() {
            const now = new Date();
            let midnightEST = new Date(now.toLocaleString('en-US', { timeZone: 'America/New_York' }));
            
            // Set to midnight EST
            midnightEST.setHours(24, 0, 0, 0); 
            // If it's past midnight EST, set to next day's midnight
            if (midnightEST <= now) {
                midnightEST.setDate(midnightEST.getDate() + 1);
            }

            let timeLeft = midnightEST - now;
            let hours = Math.floor((timeLeft / (1000 * 60 * 60)) % 24);
            let minutes = Math.floor((timeLeft / 1000 / 60) % 60);
            let seconds = Math.floor((timeLeft / 1000) % 60);

            document.getElementById('countdown').textContent = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;

            setTimeout(updateCountdown, 1000);
        }

        // Start the countdown immediately rather than waiting for the page to fully load
        window.onload = updateCountdown;
    </script>
</body>
</html>
