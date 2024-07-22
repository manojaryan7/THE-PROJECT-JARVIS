<!DOCTYPE html>
<html lang="en">
<head>
      <title>Speech Recognition</title>
</head>
<body>
      <button id = "start" onclick="startRecognition()">Start Recognition</button>
      <button id = "end" onclick="stopRecognition()">Stop Recognition</button>
      <p id = "output"></p>

      <script>
            const output = document.getElementById('output');
            let recognition;

            function startRecognition() {
                  recognition = new webkitSpeechRecognition() || new SpeechRecognition();
                  recognition.lang = 'en-US';
                  recognition.continuous = true;

                  recognition.onresult = function(event) {
                  const transcript = event.results[event.results.length - 1][0].transcript; 
                  output.textContent += transcript;                       
                  };

            recognition.onend = function() {
                  recognition.start();
            };
            recognition.start();
            }

            function stopRecognition() {
                  recognition.stop();
                  output.innerHTML = ""
            }
      </script>
</body>
</html>
