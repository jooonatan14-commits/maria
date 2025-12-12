# maria
 Um Assistente Virtual feito Em Python.

 Foco:
    Fácil de aprender.
    Rápido e expansível.

Técnologias:
    Reconhecimento de voz: (Google para reconhecimento online, Vosk para reconhecimento offline)
    Síntese de voz:
    Algum de tipo IA:
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Luna - Assistente de Voz</title>
  <style>
    .pulse {animation:pulse 1.2s infinite;}
    @keyframes pulse {0%{transform:scale(1);}50%{transform:scale(1.08);}100%{transform:scale(1);}}
    .mic-btn {font-size:22px; padding:14px 24px; border-radius:15px; background:#6dd6ff;}
    .mic-btn:hover {background:#4ec8ff;}
    .bubble {background:white; color:black; padding:12px 18px; border-radius:15px; display:inline-block; margin-top:15px;}
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(#4f59ff, #1b1e3c);
      color: white;
      text-align: center;
      padding: 40px;
    }
    #container {
      background: rgba(255,255,255,0.1);
      padding: 30px;
      border-radius: 20px;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 0 20px rgba(0,0,0,0.3);
    }
    button {
      padding: 12px 20px;
      font-size: 18px;
      border: none;
      background: #00d0ff;
      border-radius: 10px;
      cursor: pointer;
    }
    button:hover {
      background: #00a4cc;
    }
  .avatar-container { margin-top:20px; }
.avatar { width:140px; border-radius:50%; box-shadow:0 0 15px rgba(255,255,255,0.4);} 
#lunaText { font-size:20px; margin:15px; }
button { transition:0.2s; }
button:active { transform:scale(0.95);} 
</style>
</head>
<body>
  <div id="container">
    <h1>Assistente Luna 🌙✨ 🌙</h1>
    <p>Clique para falar com a Luna!</p>
    <button onclick="startListening()">🎤 Falar com a Luna</button>
    <p id="texto"></p>
  </div>  <script>
    const synth = window.speechSynthesis;
    const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
    recognition.lang = 'pt-BR';

    function falar(texto) {
      const fala = new SpeechSynthesisUtterance(texto);
      fala.lang = 'pt-BR';
      synth.speak(fala);
    }

    function startListening() {
      falar('Olá! Estou ouvindo você.');
      recognition.start();
    }

    recognition.onresult = function(event) {
      const comando = event.results[0][0].transcript.toLowerCase();
      document.getElementById('lunaText').innerText = 'Você disse: ' + comando;
      document.querySelector('.avatar').classList.add('pulse');

      if (comando.includes('oi') || comando.includes('olá')) {
        falar('Oi! Estou aqui com você!');
      }
      else if (comando.includes('estudo') || comando.includes('ajuda')) {
        falar('Claro! Me diga qual matéria você quer estudar.');
      }
      else if (comando.includes('companhia')) {
        falar('Eu adoro fazer companhia pra você. O que você quer conversar?');
      }
      else if (comando.includes('matemática')) {
        falar('Vamos estudar matemática! Qual parte você quer aprender?');
      }
      else if (comando.includes('história')) {
        falar('História é fascinante! Qual período você quer saber?');
      }
      else if (comando.includes('motiva')) {
        falar('Você é capaz de coisas incríveis. Eu acredito em você!');
      }
      else {
        falar('Desculpa, não entendi. Pode repetir?');
      }
      setTimeout(()=>{
          document.querySelector('.avatar').classList.remove('pulse');
      },1200);
    }
      else if (comando.includes('estudo') || comando.includes('ajuda')) {
        falar('Claro! Me diga qual matéria você quer estudar.');
      }
      else if (comando.includes('companhia')) {
        falar('Eu adoro fazer companhia pra você. O que você quer conversar?');
      }
      else {
        falar('Desculpa, não entendi. Pode repetir?');
      }
    }
  </script>  <div class="avatar-container">
    <img src="https://cdn-icons-png.flaticon.com/512/9131/9131529.png" class="avatar" />
    <p id="lunaText">Olá! Eu sou a Luna 🌙</p>
    <button onclick="startListening()">🎤 Falar com a Luna</button>
  </div>
</body>
</html>
