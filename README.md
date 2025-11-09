<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Simple Chatbot</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: #1e1e1e;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }
    .chat-container {
        background: #fff;
        width: 350px;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 0 15px rgba(0,0,0,0.3);
    }
    #chat-box {
        height: 400px;
        overflow-y: auto;
        padding: 10px;
        background: #f2f2f2;
    }
    .message {
        margin: 8px 0;
        padding: 10px;
        border-radius: 5px;
        max-width: 80%;
    }
    .user {
        background: #007bff;
        color: white;
        margin-left: auto;
    }
    .bot {
        background: #e0e0e0;
        color: black;
    }
    .input-area {
        display: flex;
        border-top: 1px solid #ccc;
    }
    input {
        flex: 1;
        padding: 10px;
        border: none;
        outline: none;
    }
    button {
        padding: 10px 15px;
        border: none;
        background: #007bff;
        color: white;
        cursor: pointer;
    }
</style>

</head>
<body>

<div class="chat-container">
    <div id="chat-box"></div>
    <div class="input-area">
        <input type="text" id="user-input" placeholder="Type your message...">
        <button onclick="sendMessage()">Send</button>
    </div>
</div>

<script>
function sendMessage() {
    const input = document.getElementById("user-input");
    const message = input.value.trim();
    if (message === "") return;

    displayMessage(message, "user");
    input.value = "";

    setTimeout(() => {
        const reply = getBotResponse(message.toLowerCase());
        displayMessage(reply, "bot");
    }, 600);
}

function displayMessage(text, sender) {
    const chatBox = document.getElementById("chat-box");
    const msg = document.createElement("div");

    msg.className = `message ${sender}`;
    msg.innerText = text;

    chatBox.appendChild(msg);
    chatBox.scrollTop = chatBox.scrollHeight;
}

function getBotResponse(input) {
    if (input.includes("hello") || input.includes("hi")) {
        return "Hello! How can I help you? 😊";
    } else if (input.includes("name")) {
        return "I am SimpleBot 🤖";
    } else if (input.includes("bye")) {
        return "Goodbye! 👋";
    } else {
        return "Sorry, I don't understand that yet 🙃";
    }
}
</script>

</body>
</html>

