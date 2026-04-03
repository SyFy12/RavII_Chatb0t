<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mobile JS Chatbot</title>
    <style>
        /* CSS: Making it look like a mobile app */
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; background-color: #e5ddd5; display: flex; flex-direction: column; height: 100vh; }
        #header { background: #075e54; color: white; padding: 15px; text-align: center; font-size: 1.2rem; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
        #chat-box { flex: 1; overflow-y: auto; padding: 20px; display: flex; flex-direction: column; gap: 10px; }
        
        /* Message Bubbles */
        .message { padding: 10px 15px; border-radius: 10px; max-width: 80%; font-size: 16px; word-wrap: break-word; }
        .bot-msg { align-self: flex-start; background: white; border-bottom-left-radius: 2px; }
        .user-msg { align-self: flex-end; background: #dcf8c6; border-bottom-right-radius: 2px; }

        /* Input Area */
        #input-container { display: flex; padding: 10px; background: #f0f0f0; border-top: 1px solid #ccc; }
        input { flex: 1; padding: 12px; border: none; border-radius: 25px; outline: none; font-size: 16px; }
        button { background: #075e54; color: white; border: none; border-radius: 50%; width: 45px; height: 45px; margin-left: 10px; cursor: pointer; font-size: 1.2rem; }
    </style>
</head>
<body>

<div id="header">JS Chatbot Instance</div>
<div id="chat-box">
    <div class="message bot-msg">Chatbot: Hi there! I'm your chatbot. Type 'quit' to exit.</div>
</div>

<div id="input-container">
    <input type="text" id="user-input" placeholder="Type a message..." autofocus>
    <button id="send-btn">➤</button>
</div>

<script>
    const chatBox = document.getElementById('chat-box');
    const userInput = document.getElementById('user-input');
    const sendBtn = document.getElementById('send-btn');

    function processInput() {
        const rawText = userInput.value.trim();
        if (rawText === "") return;

        // Display User Message
        appendMessage(rawText, 'user-msg');
        userInput.value = "";

        // Process Logic (Translated from your Java code [cite: 3, 4, 5, 6, 7])
        const cleanInput = rawText.toLowerCase();
        let response = "";

        if (cleanInput === "quit") {
            response = "Chatbot: Goodbye! Have a great day!"; [cite: 3]
        } else {
            switch (cleanInput) {
                case "hello":
                case "hi":
                case "hey":
                    response = "Chatbot: Hello! How can I assist you today?"; [cite: 4]
                    break;
                case "how are you":
                    response = "Chatbot: I'm just a program, but I'm doing great! How about you?"; [cite: 5]
                    break;
                case "what is your name":
                    response = "Chatbot: I'm your friendly chatbot. What's your name?"; [cite: 6]
                    break;
                default:
                    response = "Chatbot: I'm not sure I understand. Can you rephrase?"; [cite: 7]
                    break;
            }
        }

        // Delay response slightly for a "human" feel
        setTimeout(() => {
            appendMessage(response, 'bot-msg');
        }, 600);
    }

    function appendMessage(text, className) {
        const msgDiv = document.createElement('div');
        msgDiv.classList.add('message', className);
        msgDiv.innerText = text;
        chatBox.appendChild(msgDiv);
        chatBox.scrollTop = chatBox.scrollHeight; // Auto-scroll to bottom
    }

    // Listeners for Send click and Enter key
    sendBtn.addEventListener('click', processInput);
    userInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') processInput();
    });
</script>

</body>
</html>
