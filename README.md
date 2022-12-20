<html lang="en">

<head>
  <meta charset="utf-8">
  <title>Subway Surfers</title>
   <link rel="stylesheet" href="style.css" type="text/css">
</head>

<body>
  <canvas id="glcanvas" width="1024" height="800"></canvas>

  <div id="ModalBox" class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <p class='game_title'></p>
        <p class="game_score" style="font-size: 20px";></p>
        <div class="modal-footer" id="arrow" onmouseover="" style="cursor:pointer;"></div>
        <p class="play_again" id="play_again" onmouseover="" style="font-size: 25px;cursor:pointer;margin-left: 29%;"></p>
      </div>
    </div>
  </div>


  <div id="GameScore" class="score">
    <div class="score_content">
      <div class="score_box">
        <h1>Score</h2>
          <h2 class="score_gain"></h2>
      </div>
    </div>
  </div>

</body>

<script type="text/javascript">
  var modal = document.getElementById('ModalBox');
  var score = document.getElementById('GameScore');

  var music;
  music = new sound("assets/bgmusic.mp3");

  function start() {
    modal.style.display = "flex";
    x = document.querySelector(".game_title");
    x.textContent = "Subway Surfers";
    y = document.querySelector(".play_again");
    y.style.display = "none";
  }

  document.getElementById("arrow").addEventListener("click", start_box);
  document.getElementById("play_again").addEventListener("click", restart_game);

  function start_box() {
    game_start = true;
    music.play();
    modal.style.display = "none";
    score.style.display = "flex";
  }

  function restart_game() {
    document.location.reload();
  }

  function update_score() {
    x = document.querySelector(".score_gain");
    x.textContent = objects[0].score;
  }

  function Game_over() {
    modal.style.display = "flex";
    score.style.display = "none";

    x = document.querySelector(".game_title");
    if(game_over)
      x.textContent = "Game Over";
    else if(finish)
      x.textContent = "You Won!";

    y = document.querySelector(".game_score");
    y.textContent = "Your score: " + objects[0].score;
    y.style.display = "flex";

    z = document.querySelector(".modal-footer");
    z.style.display = "none";

    w = document.querySelector(".play_again");
    w.style.display = "flex";
    w.textContent = "Play Again"

    music.stop();
  }

  function sound(src) {
    this.sound = document.createElement("audio");
    this.sound.src = src;
    this.sound.setAttribute("preload", "auto");
    this.sound.setAttribute("controls", "none");
    this.sound.style.display = "none";
    document.body.appendChild(this.sound);
    this.play = function() {
      this.sound.play();
    }
    this.stop = function() {
      this.sound.pause();
    }
  }

  start();

</script>
<script src="./libs/gl-matrix.js"></script>
<script src="./libs/jquery-3.3.1.min.js"></script>
<script src="./libs/webgl-utils.js"></script>

<script src="./src/utility.js"></script>
<script src="./src/camera.js"></script>
<script src="./src/texture.js"></script>
<script src="./src/finishline.js"></script>
<script src="./src/boost.js"></script>
<script src="./src/obstacle.js"></script>
<script src="./src/barrier.js"></script>
<script src="./src/coin.js"></script>
<script src="./src/ground.js"></script>
<script src="./src/track.js"></script>
<script src="./src/police.js"></script>
<script src="./src/player.js"></script>
<script src="./src/wall.js"></script>
<script src="./src/keyhandler.js"></script>
<script src="./src/draw.js"></script>
<script src="./src/main.js"></script>

</html>

