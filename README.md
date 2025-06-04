<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Conversational AI Agent</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    .chat-container {
      max-width: 600px;
      margin: 50px auto;
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 0 5px rgba(0,0,0,0.3);
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }
    .chat-header {
      background: #007BFF;
      color: white;
      padding: 10px;
      text-align: center;
      font-size: 20px;
    }
    .chat-messages {
      flex: 1;
      padding: 10px;
      overflow-y: auto;
      height: 400px;
    }
    .message {
      margin: 10px 0;
      padding: 10px;
      border-radius: 5px;
    }
    .user-message {
      text-align: right;
      background: #d1ecf1;
      color: #0c5460;
    }
    .agent-message {
      text-align: left;
      background: #e2e3e5;
      color: #383d41;
    }
    .chat-input {
      display: flex;
      padding: 10px;
      border-top: 1px solid #ddd;
    }
    .chat-input input {
      flex: 1;
      padding: 10px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .chat-input button {
      padding: 10px 15px;
      font-size: 16px;
      background: #007BFF;
      color: white;
      border: none;
      border-radius: 5px;
      margin-left: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="chat-header">Conversational AI Agent</div>
    <div id="chatMessages" class="chat-messages">
      <!-- Chat messages will appear here -->
    </div>
    <div class="chat-input">
      <input type="text" id="userInput" placeholder="Type your message here..." />
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>

  <script>
    // Utility function to append a new message to the chat window
    function appendMessage(content, className) {
      const messageElement = document.createElement("div");
      messageElement.classList.add("message", className);
      messageElement.innerText = content;
      const chatMessages = document.getElementById("chatMessages");
      chatMessages.appendChild(messageElement);
      // Auto-scroll to the bottom of the message window
      chatMessages.scrollTop = chatMessages.scrollHeight;
    }

    // Basic conversational logic using keyword matching
    function getAIResponse(userMessage) {
      const message = userMessage.toLowerCase();
      if (message.includes("hello") || message.includes("hi")) {
        return "Hello! How can I assist you today?";
      } else if (message.includes("how are you")) {
        return "I'm just a conversational AI, but I'm here and ready to help!";
      } else if (message.includes("help")) {
        return "Sure! What can I do for you?";
      } else if (message.includes("bye")) {
        return "Goodbye! Feel free to chat anytime.";
      } else {
        return "That's interesting, could you elaborate a bit more?";
      }
    }

    // Process user message and simulate a slight delay for the AI response
    function sendMessage() {
      const userInput = document.getElementById("userInput");
      const userMessage = userInput.value.trim();
      if (userMessage === "") return;
      appendMessage("You: " + userMessage, "user-message");
      userInput.value = "";
      setTimeout(() => {
        const aiResponse = getAIResponse(userMessage);
        appendMessage("Agent: " + aiResponse, "agent-message");
      }, 500); // Delay to mimic processing time
    }
  </script>
</body>
</html>
