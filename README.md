# Cassie-Voice-Assistant
<!DOCTYPE html>
<html lang="en">

<!-- Head Starts -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Virtual Assistant Sonu</title>
    <style>
        body {
            background-color: cyan;
        }

        h1 {
            color: rgb(0, 0, 0);
        }
    </style>
</head>

<!-- Head Ends -->

<!-- Body Starts -->

    #Body Starts 
<body onload="greeting()">
    <h1> Hello <br> I am Sonu , Your Virtual Assistant , How Can I Help You ?</h1>
    <div class="wrapper">
        <div class="actions" >
            <button id="start" style="width: 100px; height: 50px;">Talk</button>
            <button id="end" style="width: 100px; height: 50px;">End</button>
        </div>
        <div id="transcript">
        </div>
    </div>
    <script>
        window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

        const recognition = new SpeechRecognition();
        recognition.interimResults = true;
        const transcript_element = document.getElementById("transcript");
        const talk_button = document.getElementById("start");
        const end_button = document.getElementById("end");

        let p = document.createElement("p");
        transcript_element.appendChild(p);

        recognition.addEventListener("result", (e) => {
            const transcript = Array.from(e.results)
                .map(result => result[0])
                .map(result => result.transcript)
                .join("");
            p.textContent = transcript;
            if (e.results[0].isFinal) {
                p = document.createElement("p")
                p.textContent = transcript;
                transcript_element.appendChild(p);
                p.textContent = "";

                if (transcript.includes("YouTube")) {
                    window.open('https://www.youtube.com/')
                }
                if(transcript.includes("Google")){
                    window.open('https://www.google.com')
                }
                if(transcript.includes("music")){
                    window.open('https://www.spotify.com')
                }
            }

        });

        function greeting() {
            alert("Have A Good Day !")
        }
        recognition.addEventListener("end", () => {
            end_button.disabled = false;
            talk_button.disabled = true;
        });
        talk_button.addEventListener("click", () => {
            end_button.disabled = false;
            talk_button.disabled = true;
            recognition.start();
        });
        end_button.addEventListener("click", () => {
            end_button.disabled = true;
            talk_button.disabled = false;
            recognition.stop();
        });

    </script>
</body>

<!-- Body Ends -->

</html>
