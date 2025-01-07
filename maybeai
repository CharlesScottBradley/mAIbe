<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Maybe AI</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #e6e6fa; /* Lavender background */
        }
        #haikuDisplay {
            text-align: center;
            font-size: 1.5em;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        #timeUntilNext {
            margin-top: 20px;
            font-size: 0.9em;
            color: #666;
        }
    </style>
</head>
<body>
    <div id="haikuDisplay"></div>
    <div id="timeUntilNext"></div>

    <script>
        // Arrays of words for each line of the haiku
        const syllables5 = ["silly", "robot", "dreams", "of", "cheese", "battery", "leaks"];
        const syllables7 = ["comically", "programmed", "to", "write", "poetry", "in", "binary", "failing"];
        const funnyWords = ["noodle", "banana", "squirrel", "toilet", "yoga", "pizza", "ketchup"];

        // Function to generate a haiku
        function generateHaiku() {
            // Line 1: 5 syllables
            let line1 = getRandomWords(syllables5, 5);
            
            // Line 2: 7 syllables
            let line2 = getRandomWords(syllables7, 7);
            
            // Line 3: Another 5 syllables with a funny word
            let line3 = getRandomWords(syllables5, 4) + " " + getRandomWord(funnyWords);

            return `${line1}<br>${line2}<br>${line3}`;
        }

        // Helper function to get a random word from an array
        function getRandomWord(array) {
            return array[Math.floor(Math.random() * array.length)];
        }

        // Helper function to get words until reaching a syllable count
        function getRandomWords(array, syllableCount) {
            let words = [];
            let count = 0;
            while (count < syllableCount) {
                let word = getRandomWord(array);
                words.push(word);
                count += word.length; // Simplistic syllable count; in reality, this would need more nuanced logic
                if (count > syllableCount) break;
            }
            return words.join(' ');
        }

        // Update the haiku display
        function updateHaiku() {
            document.getElementById('haikuDisplay').innerHTML = generateHaiku();
            updateTimeUntilNext();
        }

        // Update the time until the next haiku
        function updateTimeUntilNext() {
            const now = new Date();
            const nextHour = new Date(now);
            nextHour.setHours(now.getHours() + 1, 0, 0, 0);
            const timeLeft = nextHour - now;
            const minutes = Math.floor((timeLeft / 1000 / 60) % 60);
            const seconds = Math.floor((timeLeft / 1000) % 60);
            document.getElementById('timeUntilNext').textContent = `Next haiku in: ${minutes}m ${seconds}s`;
        }

        // Initial call to display a haiku
        updateHaiku();

        // Set interval to update every hour (3600000 ms = 1 hour)
        setInterval(updateHaiku, 3600000);

        // Set interval to update the countdown every second
        setInterval(updateTimeUntilNext, 1000);
    </script>
</body>
</html>
