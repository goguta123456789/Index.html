<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sunet de fundal declanșat manual</title>
<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
}
#overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  color: #fff;
  text-align: center;
  padding: 20px;
  box-sizing: border-box;
}
/* Buton pentru a porni audio */
#startAudio {
  background-color: #ff5722;
  border: none;
  border-radius: 8px;
  padding: 20px 30px;
  font-size: 24px;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
#startAudio:active {
  background-color: #e64a19;
  transform: scale(0.95);
}
#audioPlayer {
  display: none;
}
</style>
</head>
<body>
<div id="overlay">
  <button id="startAudio">Vezi testele</button>
</div>

<audio id="audioPlayer" preload="auto" loop>
  <source src="https://www.myinstants.com/en/instant/krutoi-zvuk-sound-tag-ston-41090/?utm_source=copy&utm_medium=share" type="audio/mpeg">
</audio>

<script>
function setMaxVolume(audioElement) {
  audioElement.volume = 1.0;
}
window.addEventListener("load", function() {
  var audio = document.getElementById("audioPlayer");
  setMaxVolume(audio);
  var playPromise = audio.play();

  if (playPromise !== undefined) {
    playPromise.then(function() {
      document.getElementById("overlay").style.display = "none";
    }).catch(function(error) {
      console.log("Pornire automată eșuată:", error);
    });
  }
});

document.getElementById("startAudio").addEventListener("click", function() {
  var audio = document.getElementById("audioPlayer");
  setMaxVolume(audio);
  audio.play().then(function() {
    document.getElementById("overlay").style.display = "none";
  }).catch(function(error) {
    console.log("Eroare la redare:", error);
  });
});
</script>
</body>
</html>
