<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FunChat</title>

<style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
        background: #111;
        font-family: Arial, sans-serif;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        color: #00eaff;
    }
    h1 { margin-bottom: 15px; }
    .chat-container {
        width: 350px;
        background: #181818;
        border-radius: 12px;
        padding: 15px;
    }
    #chat-box {
        height: 300px;
        background: #1e1e1e;
        border-radius: 8px;
        padding: 10px;
        overflow-y: auto;
        color: #fff;
    }
    .message {
        margin: 6px 0;
        padding: 8px;
        border-radius: 6px;
        font-size: 14px;
        max-width: 80%;
    }
    .user { background: #007bff; margin-left: auto; color: #fff; }
    .bot { background: #333; color: #00eaff; }
    .input-area { display: flex; margin-top: 10px; }
    input {
        flex: 1;
        padding: 10px;
        background: #222;
        border: none;
        color: white;
        border-radius: 6px 0 0 6px;
    }
    button {
        padding: 10px 15px;
        background: #00eaff;
        border: none;
        font-weight: bold;
        cursor: pointer;
        color: #000;
        border-radius: 0 6px 6px 0;
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
    const box = document.getElementById("chat-box");
    const input = document.getElementById("user-input");
    const msg = input.value.trim();
    if (!msg) return;

    addMessage(msg, "user");
    input.value = "";

    setTimeout(() => {
        addMessage(getReply(msg.toLowerCase()), "bot");
    }, 500);
}

function addMessage(text, sender) {
    const box = document.getElementById("chat-box");
    const div = document.createElement("div");
    div.className = "message " + sender;
    div.innerText = text;
    box.appendChild(div);
    box.scrollTop = box.scrollHeight;
}

function getReply(text) {
    if (text.includes("hello") || text.includes("hi")) return "Hey! 🤖";
    if (text.includes("name")) return "I am FunChat Bot!";
    if (text.includes("bye")) return "Bye 👋";
    return "Still learning 😄";
}
</script>
</body>
</html>
