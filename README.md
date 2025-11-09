<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FunChat</title>

<style>
    body {
        background: #111;
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        flex-direction: column;
        color: #00eaff;
    }
    h1 {
        margin-bottom: 15px;
        font-size: 40px;
    }
    .chat-container {
        width: 350px;
        background: #181818;
        border-radius: 12px;
        padding: 15px;
        border: 1px solid #333;
    }
    #chat-box {
        height: 350px;
        overflow-y: auto;
        background: #1e1e1e;
        border-radius: 8px;
        padding: 10px;
        color: #fff;
    }
    .message {
        margin: 8px 0;
        padding: 10px;
        border-radius: 6px;
        max-width: 80%;
        font-size: 14px;
    }
    .user {
        background: #007bff;
        margin-left: auto;
        color: #fff;
    }
    .bot {
        background: #333;
        color: #00eaff;
    }
    .input-area {
        display: flex;
        margin-top: 10px;
    }
    input {
        flex: 1;
        padding: 10px;
        border: none;
        background: #222;
        color: #fff;
        border-radius: 6px 0 0 6px;
        outline: none;
    }
    button {
        padding: 10px 20px;
        border: none;
        background: #00eaff;
        color: #000;
        cursor: pointer;
        border-radius: 0 6px 6px 0;
        font-weight: bold;
    }
</style>
</head>
<body>

<h1>FunChat</h1>

<div class="chat-container">
    <div id="chat-box"></div>

    <div class="input-area">
        <input type="text" id="user-input" placeholder="Type a message...">
        <button onclick="sendMessage()">Send</button>
    </div>
</div>

<script>
function sendMessage() {
    const input = document.getElementById("user-input");
    const message = input.value.trim();
    if (!message) return;

    showMessage(message, "user");
    input.value = "";
    
    setTimeout(() => {
        showMessage(getReply(message.toLowerCase()), "bot");
    }, 500);
}

function showMessage(text, sender) {
    const box = document.getElementById("chat-box");
    const msg = document.createElement("div");
    msg.className = "message " + sender;
    msg.textContent = text;
    box.appendChild(msg);
    box.scrollTop = box.scrollHeight;
}

function getReply(text) {
    if (text.includes("hi") || text.includes("hello")) return "Hello! 👋";
    if (text.includes("name")) return "I am FunChat Bot 🤖";
    if (text.includes("bye")) return "Bye! 👋";
    return "I am still learning 😄";
}
</script>

</body>
</html>
