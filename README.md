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
    } 
    else if (input.includes("name")) {
        return "I am SimpleBot 🤖";
    }
    else if (input.includes("bye")) {
        return "Goodbye! 👋";
    }
    else {
        return "Sorry, I don't understand that yet 🙃";
    }
}
