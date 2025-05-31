<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>I Love You Prachi</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      color: white;
      text-align: center;
      background: black;
      overflow: hidden;
    }
    .background {
      position: fixed;
      top: 0;
      left: 0;
      height: 100vh;
      width: 100vw;
      z-index: -1;
      animation: slide 60s infinite;
      background-size: cover;
      background-position: center;
    }
    @keyframes slide {
      0% { background-image: url('https://images.unsplash.com/photo-1503454537195-1dcabb73ffb9'); }
      25% { background-image: url('https://images.unsplash.com/photo-1607746882042-944635dfe10e'); }
      50% { background-image: url('https://images.unsplash.com/photo-1575311373939-1a1aaecd4306'); }
      75% { background-image: url('https://images.unsplash.com/photo-1592814029861-6db60aa2f68e'); }
      100% { background-image: url('https://images.unsplash.com/photo-1503454537195-1dcabb73ffb9'); }
    }
    .content {
      margin-top: 15vh;
    }
    .text {
      font-size: 2.2rem;
      padding: 15px 25px;
      background-color: rgba(0, 0, 0, 0.5);
      border-radius: 15px;
      display: inline-block;
      animation: fade 3s ease-in-out;
      box-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
    }
    @keyframes fade {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
    .youtube {
      position: absolute;
      width: 0;
      height: 0;
      visibility: hidden;
    }
  </style>
</head>
<body>
  <div class="background"></div>
  <div class="content" id="loveMessages"></div>

  <!-- ONLY your YouTube song -->
  <div class="youtube">
    <iframe width="0" height="0"
      src="https://www.youtube.com/embed/qpIdoaaPa6U?autoplay=1&loop=1&playlist=qpIdoaaPa6U"
      frameborder="0"
      allow="autoplay"
      allowfullscreen></iframe>
  </div>

  <script>
    const messages = [
      ["I love you Prachi", "English"],
      ["मैं तुमसे प्यार करता हूँ Prachi", "Hindi"],
      ["Je t'aime Prachi", "French"],
      ["Te amo Prachi", "Spanish"],
      ["Ich liebe dich Prachi", "German"],
      ["Ti amo Prachi", "Italian"],
      ["Eu te amo Prachi", "Portuguese"],
      ["Я тебя люблю Prachi", "Russian"],
      ["愛してる Prachi", "Japanese"],
      ["我爱你 Prachi", "Chinese (Simplified)"],
      ["사랑해요 Prachi", "Korean"],
      ["Ik hou van jou Prachi", "Dutch"],
      ["Jeg elsker deg Prachi", "Norwegian"],
      ["Kocham cię Prachi", "Polish"],
      ["Dooset daram Prachi", "Persian"],
      ["Ani ohev otach Prachi", "Hebrew (Male)"],
      ["Ani ohevet otcha Prachi", "Hebrew (Female)"],
      ["Ami tomake bhalobashi Prachi", "Bengali"],
      ["Seni seviyorum Prachi", "Turkish"],
      ["Mahal kita Prachi", "Filipino"],
      ["Ma timilai maya garchu Prachi", "Nepali"],
      ["Te iubesc Prachi", "Romanian"],
      ["Szeretlek Prachi", "Hungarian"],
      ["Jag älskar dig Prachi", "Swedish"],
      ["Saya cinta padamu Prachi", "Malay"],
      ["Chan rak khun Prachi", "Thai"],
      ["Kuv hlub koj Prachi", "Hmong"],
      ["Gihigugma tika Prachi", "Cebuano"],
      ["Te sakam Prachi", "Macedonian"],
      ["Te dua Prachi", "Albanian"],
      ["Volim te Prachi", "Bosnian"],
      ["Nakupenda Prachi", "Swahili"],
      ["Ez hej te dikim Prachi", "Kurdish"],
      ["A hụrụ m gị n’anya Prachi", "Igbo"],
      ["Mo nifẹ rẹ Prachi", "Yoruba"],
      ["Ngiyakuthanda Prachi", "Zulu"],
      ["Mi amas vin Prachi", "Esperanto"],
      ["T'estimo Prachi", "Catalan"],
      ["Mən səni sevirəm Prachi", "Azerbaijani"],
      ["Ich liebe dich Prachi", "Swiss German"],
      ["Au domoni iko Prachi", "Fijian"],
      ["Aloha wau ia ‘oe Prachi", "Hawaiian"],
      ["Iokwe yuk Prachi", "Marshallese"],
      ["S'agapo Prachi", "Greek"],
      ["Me te quiero Prachi", "Spanglish"],
      ["Rakastan sinua Prachi", "Finnish"],
      ["Volim te Prachi", "Serbian"],
      ["Ljubim te Prachi", "Slovenian"],
      ["Main tuhanu pyar karda haan Prachi", "Punjabi"],
      ["Tôi yêu bạn Prachi", "Vietnamese"],
      ["Eg elska teg Prachi", "Faroese"],
      ["Rwy'n dy garu di Prachi", "Welsh"],
      ["Is breá liom tú Prachi", "Irish"],
      ["T'estimi Prachi", "Occitan"],
      ["Jeg elsker deg Prachi", "Danish"],
      ["Mi love yuh Prachi", "Jamaican Patois"],
      ["Mwen renmen ou Prachi", "Haitian Creole"],
      ["Ah lav yu Prachi", "Pidgin English"],
      ["Mahal kita ng sobra Prachi", "Taglish"],
      ["Mo ni fe re gan Prachi", "Nigerian English"],
      // Add more up to 200 if needed
    ];

    const container = document.getElementById("loveMessages");
    let index = 0;
    function showMessage() {
      const [text, lang] = messages[index];
      container.innerHTML = `<div class="text">${text}<br><small>(${lang})</small></div>`;
      index = (index + 1) % messages.length;
    }

    setInterval(showMessage, 3000);
    showMessage();
  </script>
</body>
</html>
