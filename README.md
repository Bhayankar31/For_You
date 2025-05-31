<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>I Love You, Prachi - In Every Language</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ffdde1, #ee9ca7);
      font-family: 'Segoe UI', sans-serif;
      color: white;
      text-align: center;
      overflow: hidden;
    }

    h1 {
      font-size: 3em;
      max-width: 90vw;
      text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
      animation: fadeIn 2s ease-in-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }
  </style>
</head>
<body>

  <h1 id="message">I love you, Prachi ❤️</h1>

  <script>
    const messages = [
      "I love you, Prachi ❤️", // English
      "Je t'aime, Prachi ❤️", // French
      "Te amo, Prachi ❤️", // Spanish
      "Ich liebe dich, Prachi ❤️", // German
      "Ti amo, Prachi ❤️", // Italian
      "Eu te amo, Prachi ❤️", // Portuguese
      "Я тебя люблю, Prachi ❤️", // Russian
      "我爱你, Prachi ❤️", // Chinese (Simplified)
      "愛してる, Prachi ❤️", // Japanese
      "사랑해, Prachi ❤️", // Korean
      "मैं तुमसे प्यार करता हूँ, Prachi ❤️", // Hindi
      "أنا أحبك, Prachi ❤️", // Arabic
      "Kocham cię, Prachi ❤️", // Polish
      "Seni seviyorum, Prachi ❤️", // Turkish
      "Ik hou van jou, Prachi ❤️", // Dutch
      "Jeg elsker deg, Prachi ❤️", // Norwegian
      "Jag älskar dig, Prachi ❤️", // Swedish
      "Jeg elsker dig, Prachi ❤️", // Danish
      "Εγώ σε αγαπώ, Prachi ❤️", // Greek
      "Mahal kita, Prachi ❤️", // Filipino
      "Nakupenda, Prachi ❤️", // Swahili
      "Ek het jou lief, Prachi ❤️", // Afrikaans
      "Te iubesc, Prachi ❤️", // Romanian
      "Volim te, Prachi ❤️", // Serbian/Croatian/Bosnian
      "Tôi yêu bạn, Prachi ❤️", // Vietnamese
      "Anh yêu em, Prachi ❤️", // Vietnamese (male to female)
      "Em yêu anh, Prachi ❤️", // Vietnamese (female to male)
      "Ich liebe dich, Prachi ❤️", // Swiss German
      "Mo nifẹ rẹ, Prachi ❤️", // Yoruba
      "Ndinokuda, Prachi ❤️", // Shona
      "Ngo oiy, Prachi ❤️", // Cantonese
      "S'agapo, Prachi ❤️", // Greek (spoken)
      "Ich liebe dich, Prachi ❤️", // Luxembourgish
      "Tha gaol agam ort, Prachi ❤️", // Scottish Gaelic
      "Tá grá agam duit, Prachi ❤️", // Irish
      "Aloha wau ia 'oe, Prachi ❤️", // Hawaiian
    ];

    let index = 0;
    const msgElement = document.getElementById("message");

    function showNextMessage() {
      msgElement.style.opacity = 0;
      setTimeout(() => {
        msgElement.innerText = messages[index];
        msgElement.style.opacity = 1;
        index = (index + 1) % messages.length;
      }, 500);
    }

    setInterval(showNextMessage, 2500);
  </script>

</body>
</html>
