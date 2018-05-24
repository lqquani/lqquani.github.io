<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=0">
  <title>riot-snake</title>
  <style>
    * {
      font-family: "Lucida Grande";
    }
    #gameContainer, #pastScores {
      width: 600px;
      float: left;
    }
    .row {
      height: 26px;
    }
    .column {
      border: 1px solid white;
      width: 24px;
      height: 24px;
      display: inline-block;
    }
    .item-board{
      background-color: #000;
    }
    .item-fruit{
      background-color: #E80505;
    }
    .item-head{
      background-color: #078F00;
    }
    .item-body{
      background-color: #0DFF00;
    }
    .item-tail{
      background-color: #0DFF00;
    }
    #btn {
      width: 120px;
      padding: 10px;
      margin-top: 5px;
      text-align: center;
      background-color: black;
      color: white;
    }
    #btn:hover {
      color: red;
      cursor: pointer;
    }
  </style>
</head>

<body>

<snake-board>
</snake-board>

<a href="https://lqquani.github.io/" target="_blank">
  <img style="position: absolute; top: 0; right: 0; border: 0;" src="https://camo.githubusercontent.com/38ef81f8aca64bb9a64448d0d70f1308ef5341ab/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6461726b626c75655f3132313632312e706e67" alt="Fork me on GitHub" data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_darkblue_121621.png">
</a>

<script src="http://cdn.rawgit.com/muut/riotjs/master/riot.min.js"></script>

<script id="snake.tpl.html" type="riot/type">
  <div id="gameContainer">
    <h3>Score: {{score}},  Max: {{maxScore}}</h3>
    <div>
      <div each="{{column, i in board}}" class="row" data-row="{{i}}">
        <div each="{{row, j in column}}" class="column {{'item-'+row.type}}" data-col="{{parent.i+'-'+j}}"></div>
      </div>
    </div>
    <div id="btn" onclick="{{startGame}}">Start Game</div>
  </div>
</script>

<script>
  riot.settings.brackets = '{{ }}';
  riot.tag('snake-board', document.getElementById('snake.tpl.html').innerHTML, function(opts){
    var self = this;
    self.board = [];
    self.snake = [];
    self.size = opts.size || 20;
    self.maxScore = 0;
    function init(){
      //init var
      self.score = 0;
      self.speed = opts.speed || 150;
      self.isPlaying = false;
      self.direction = {x: 0, y: -1};
      //init board
      self.board = [];
      for(var i = 0; i < self.size; i++) {
        var column = [];
        for (var j = 0; j < self.size; j++) {
          column.push({type: 'board'});
        }
        self.board.push(column);
      }
      //init snake
      var snake = self.snake = [];
      for (var k = 0; k < 5; k++) {
        var point = {x: 10 + k, y: 10};
        snake.push(point);
        changeType(point, 'body');
      }
      changeType(snake[0], 'head');
      changeType(snake[[k-1]], 'tail');
      resetFruit();
      self.update();
    };
    function updateBoard(){
      var nextPoint = getNextPoint();
      //if outside or snake itself
      if(isCollision(nextPoint)){
        gameOver();
      }else{
      	//isFruit
        if(nextPoint.x === self.fruit.x && nextPoint.y === self.fruit.y){
          eatFruit();
        }else{
          moveSnake();
        }
        setTimeout(updateBoard, self.speed);
      }
    };
    function getNextPoint(){
      return {
        x: self.snake[0].x + self.direction.x,
        y: self.snake[0].y + self.direction.y
      }
    };
    function isCollision(point){
      return point.x < 0 || point.y < 0 || point.x >= self.size || point.y >= self.size || self.snake.some(function(item){ return item.x === point.x && item.y === point.y; });
    };
    function resetFruit(){
      var point = {
        x: Math.floor(Math.random() * self.size),
        y: Math.floor(Math.random() * self.size)
      };
      var isSnake = self.snake.some(function(item){ return item.x === point.x && item.y === point.y; });
      self.fruit = isSnake ? resetFruit() : point;
      changeType(self.fruit, 'fruit');
      self.update();
    };
    function eatFruit(){
      self.score++;
      self.maxScore = Math.max(self.maxScore, self.score);
      if (self.score % 5 === 0) {
        self.speed -= 15;
      }
      moveSnake(true);
      resetFruit();
    };
    function moveSnake(keep){
      var snake = self.snake;
      if(!keep){
        // Remove tail
        var oldTail = snake.pop();
        changeType(oldTail, 'board');
        // Add new tail
        var newTail = snake[snake.length - 1];
        changeType(newTail, 'tail');
      }
      // Remove head
      var oldHead = snake[0];
      changeType(oldHead, 'body');
      // Add new head
      var newHead = getNextPoint();
      self.snake.unshift(newHead);
      changeType(newHead, 'head');
      self.update();
    };
    function changeType(point, type){
      self.board[point.y][point.x].type = type;
    };
    function bindEvent(){
      window.addEventListener("keyup", function(e){
        var x = self.direction.x;
        var y = self.direction.y;
        var code = e.keyCode;
        if(code === 37 && x !== 1){         //LEFT
          x = -1;
          y = 0;
        }else if(code === 39 && x !== -1){  //RIGHT
          x = 1;
          y = 0;
        }else if(code === 38 && y !== 1){   //UP
          x = 0;
          y = -1;
        }else if(code === 40 && y !== -1){  //DOWN
          x = 0;
          y = 1;
        }else if(code === 32){              //SPACE
          startGame();
        }
        self.direction = {x: x, y: y};
      });
    };
    function gameOver(){
      self.isPlaying = false;
      console.log('game over');
    };
    function startGame(){
      if(!self.isPlaying) {
        init();
        self.isPlaying = true;
        updateBoard();
      }
    };
    self.on('mount', function(){
      init();
      bindEvent();
    });
  }); 
  riot.mount('*');
</script>

</body>
</html>
