<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Playfair+Display&size=35&pause=1000&color=8FD3FF&center=true&vCenter=true&width=700&lines=Hi,+I'm+Maryam+Hisham" />
</p>


    
        <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Pink Worm Game</title>

<style>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #ffe6f1;
    font-family: Arial, sans-serif;
}

.game {
    text-align: center;
}

h1 {
    color: #ff4f9a;
    margin-bottom: 10px;
}

canvas {
    display: block;
    background: white;
    border: 4px solid #ff8fbd;
    border-radius: 15px;
}

p {
    color: #777;
}
</style>
</head>

<body>

<div class="game">

<h1>Pink Worm</h1>

<canvas id="canvas" width="400" height="400"></canvas>

<p>Use ↑ ↓ ← → to move</p>

</div>

<script>

const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const box = 20;

let worm = [
    {x: 200, y: 200},
    {x: 180, y: 200},
    {x: 160, y: 200}
];

let food = {
    x: Math.floor(Math.random() * 20) * box,
    y: Math.floor(Math.random() * 20) * box
};

let direction = "RIGHT";

document.addEventListener("keydown", function(e) {

    if (e.key === "ArrowUp" && direction !== "DOWN")
        direction = "UP";

    if (e.key === "ArrowDown" && direction !== "UP")
        direction = "DOWN";

    if (e.key === "ArrowLeft" && direction !== "RIGHT")
        direction = "LEFT";

    if (e.key === "ArrowRight" && direction !== "LEFT")
        direction = "RIGHT";
});

function draw() {

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    let head = {
        x: worm[0].x,
        y: worm[0].y
    };

    if (direction === "UP")
        head.y -= box;

    if (direction === "DOWN")
        head.y += box;

    if (direction === "LEFT")
        head.x -= box;

    if (direction === "RIGHT")
        head.x += box;

    if (
        head.x < 0 ||
        head.x >= canvas.width ||
        head.y < 0 ||
        head.y >= canvas.height
    ) {
        reset();
        return;
    }

    worm.unshift(head);

    if (
        head.x === food.x &&
        head.y === food.y
    ) {

        food = {
            x: Math.floor(Math.random() * 20) * box,
            y: Math.floor(Math.random() * 20) * box
        };

    } else {

        worm.pop();

    }

    drawFood();
    drawWorm();
}

function drawWorm() {

    worm.forEach(function(part, index) {

        ctx.beginPath();

        ctx.arc(
            part.x + 10,
            part.y + 10,
            9,
            0,
            Math.PI * 2
        );

        ctx.fillStyle =
            index === 0 ? "#ff3f91" : "#ff8fbd";

        ctx.fill();

        if (index === 0) {

            ctx.fillStyle = "white";

            ctx.beginPath();
            ctx.arc(part.x + 6, part.y + 7, 3, 0, Math.PI * 2);
            ctx.fill();

            ctx.beginPath();
            ctx.arc(part.x + 14, part.y + 7, 3, 0, Math.PI * 2);
            ctx.fill();

            ctx.fillStyle = "#222";

            ctx.beginPath();
            ctx.arc(part.x + 6, part.y + 7, 1.5, 0, Math.PI * 2);
            ctx.fill();

            ctx.beginPath();
            ctx.arc(part.x + 14, part.y + 7, 1.5, 0, Math.PI * 2);
            ctx.fill();
        }
    });
}

function drawFood() {

    ctx.beginPath();

    ctx.arc(
        food.x + 10,
        food.y + 10,
        6,
        0,
        Math.PI * 2
    );

    ctx.fillStyle = "#ff4f91";
    ctx.fill();
}

function reset() {

    worm = [
        {x: 200, y: 200},
        {x: 180, y: 200},
        {x: 160, y: 200}
    ];

    direction = "RIGHT";
}

setInterval(draw, 120);

</script>

</body>
</html>
