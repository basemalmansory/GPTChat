<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Puter.js Chat</title>
  <script src="https://js.puter.com/v2/"></script>
</head>
<body>
  <h2>مساعد الذكاء الاصطناعي</h2>
  <textarea id="chatInput" rows="4" cols="50" placeholder="اكتب رسالتك هنا..."></textarea><br>
  <button id="sendBtn">إرسال</button>
  <pre id="chatOutput"></pre>

  <script>
    const chatInput = document.getElementById("chatInput");
    const sendBtn = document.getElementById("sendBtn");
    const chatOutput = document.getElementById("chatOutput");

    sendBtn.onclick = async () => {
      const prompt = chatInput.value;
      chatInput.value = "";
      chatOutput.textContent += "أنت: " + prompt + "\n";

      try {
        const response = await puter.ai.chat(prompt);
        chatOutput.textContent += "المساعد: " + response + "\n\n";
      } catch (err) {
        chatOutput.textContent += "خطأ: " + err.message + "\n";
      }
    };
  </script>
</body>
</html>
