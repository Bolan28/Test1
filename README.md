# Test1
Test number 1
<!DOCTYPE html>
<html>
<head>
  <title>My Game</title>
</head>
<body>
  <canvas id="canvas" width="600" height="400"></canvas>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.12.1/p5.min.js"></script>
  <script>
    var canvas = document.getElementById("canvas");
    var ctx = canvas.getContext("2d");
    
    // Create a ball
    var ball = {
      x: 300,
      y: 200,
      radius: 10,
      velocityX: 5,
      velocityY: 5
    };
    
    // Create a paddle
    var paddle = {
      x: 200,
      y: 200,
      width: 100,
      height: 20
    };
    
    // Draw the ball and the paddle
    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "black";
      ctx.fillCircle(ball.x, ball.y, ball.radius);
      ctx.fillStyle = "white";
      ctx.fillRect(paddle.x, paddle.y, paddle.width, paddle.height);
      
      // Move the ball
      ball.x += ball.velocityX;
      ball.y += ball.velocityY;
      
      // Check for collisions with the walls
      if (ball.x < 0 || ball.x > canvas.width) {
        ball.velocityX *= -1;
      }
      if (ball.y < 0 || ball.y > canvas.height) {
        ball.velocityY *= -1;
      }
      
      // Check for collisions with the paddle
      if (ball.x < paddle.x + paddle.width && ball.y > paddle.y && ball.y < paddle.y + paddle.height) {
        ball.velocityX *= -1;
      }
      
      // RequestAnimationFrame to redraw the scene
      requestAnimationFrame(draw);
    }
    
    // Start the game
    start();
  </script>
</body>
</html>
