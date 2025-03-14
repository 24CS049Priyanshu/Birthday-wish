# Birthday-wish
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Wish</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            background-color: #fce4ec;
            overflow: hidden;
            position: relative;
        }
        .background-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 80px;
            font-weight: bold;
            color: rgba(255, 192, 203, 0.2);
            z-index: -1;
            white-space: nowrap;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
            position: relative;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease-in-out, transform 0.5s ease-in-out;
        }
        .visible {
            opacity: 1;
            transform: translateY(0);
        }
        .hidden {
            display: none;
        }
        .btn {
            padding: 10px 20px;
            margin: 10px;
            border: none;
            cursor: pointer;
            font-size: 16px;
            border-radius: 5px;
        }
        .btn-hello {
            background-color: #4CAF50;
            color: white;
        }
        .btn-no {
            background-color: #f44336;
            color: white;
        }
        .btn-next {
            background-color: #008CBA;
            color: white;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .message-box {
            animation: fadeIn 1s ease-in-out;
        }
    </style>
</head>
<body>
    <div class="background-text">Miss Busy</div>
    
    <div class="container visible" id="greeting">
        <h2>Hello!</h2>
        <button class="btn btn-hello" onclick="sayHello()">Hello</button>
        <button class="btn btn-no" onclick="notInterested()">Not Interested to Talk</button>
    </div>
    
    <div class="container hidden" id="message">
        <h2>🎉 Happy Birthday Bestie! 🎂🎈</h2>
        <p id="message-content" class="message-box">Hey Miss Busy,</p>
        <button class="btn btn-next" onclick="nextMessage()">Next</button>
    </div>

    <script>
        let messages = [
            "Happy Birthday! 🎉 Wishing you many, many happy returns of the day and an amazing year ahead.",
            "I have so much to tell you! First off, I know we haven't been able to talk as much as we used to, but with college keeping us both busy, there's not much we can do about it. Anyway, let’s not dwell on that!",
            "Here's something interesting—I realized that big moments in our friendship seem to happen on the 2nd of the month. The first time we talked for a long time was most likely on September 2nd, and exactly a month later, on October 2nd, we had our first call. There’s another event that falls on the 2nd, but let’s just skip that one. 😆 So, I guess the 2nd has been a lucky date for us!",
            "I've been wanting to share this with you for so long, and since I might not get a chance to say it in person, I’m writing it here.",
            "You’ll probably receive this message on March 15th at 12:00 AM—if I manage to upload it on time.",
            "And lastly, Miss Slim CA Sahiba, best of luck for your first CA exam in May! (Sorry, I forgot the exact date 🙈). Wishing you all the success and an incredible year ahead!",
            "Stay awesome! 😊🎂🎈"
        ];
        let index = 0;
        
        function sayHello() {
            document.getElementById("greeting").style.display = "none";
            let messageDiv = document.getElementById("message");
            messageDiv.classList.remove("hidden");
            setTimeout(() => messageDiv.classList.add("visible"), 100);
        }
        
        function notInterested() {
            let response = confirm("Please talk to me! 🙁");
            if (response) {
                location.reload();
            }
        }
        
        function nextMessage() {
            if (index < messages.length) {
                let messageContent = document.getElementById("message-content");
                messageContent.innerText = messages[index];
                messageContent.classList.remove("message-box");
                void messageContent.offsetWidth;
                messageContent.classList.add("message-box");
                index++;
            } else {
                alert("That's all! Taking you back to the start.");
                location.reload();
            }
        }
    </script>
</body>
</html>
