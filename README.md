<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Playfair+Display&size=35&pause=1000&color=8FD3FF&center=true&vCenter=true&width=700&lines=Hi,+I'm+Maryam+Hisham" />
</p>


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Worm Game</title>

<style>
    body {
        margin: 0;
        background: #ffeaf4;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        font-family: Arial;
    }

    .game {
        text-align: center;
    }

    h2 {
        color: #ff69a6;
    }

    canvas {
        background: #fff;
        border: 4px solid #ff8fbd;
        border-radius: 15px;
        box-shadow: 0 8px 20px #0002;
    }

    p {
        color: #777;
    }
</style>
</head>

<body>

<div class="game">
    <h2>Worm Game</h2>
    <canvas id="game" width="400" height="400"></canvas>
    <p>Use the arrow keys to move</p>
</div>

<script>

const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

const size = 20;

let worm = [
    {x: 200, y: 200},
    {x: 180, y: 200},
    {x: 160, y: 200}
];

let food = {
    x: Math.floor(Math.random() * 20) * size,
    y: Math.floor(Math.random() * 20) * size
};

let dx = size;
let dy = 0;

document.addEventListener("keydown", move);

function move(e) {

    if (e.key === "ArrowUp" && dy === 0) {
        dx = 0;
        dy = -size;
    }

    if (e.key === "ArrowDown" && dy === 0) {
        dx = 0;
        dy = size;
    }

    if (e.key === "ArrowLeft" && dx === 0) {
        dx = -size;
        dy = 0;
    }

    if (e.key === "ArrowRight" && dx === 0) {
        dx = size;
        dy = 0;
    }
}

function drawWorm() {

    worm.forEach((part, index) => {

        ctx.beginPath();
        ctx.arc(
            part.x + size / 2,
            part.y + size / 2,
            9,
            0,
            Math.PI * 2
        );

        ctx.fillStyle = index === 0 ? "#ff4f9a" : "#ff8fbd";
        ctx.fill();

        if (index === 0) {

            ctx.fillStyle = "#222";

            ctx.beginPath();
            ctx.arc(part.x + 7, part.y + 7, 2, 0, Math.PI * 2);
            ctx.fill();

            ctx.beginPath();
            ctx.arc(part.x + 14, part.y + 7, 2, 0, Math.PI * 2);
            ctx.fill();
        }
    });
}

function drawFood() {

    ctx.beginPath();

    ctx.arc(
        food.x + size / 2,
        food.y + size / 2,
        7,
        0,
        Math.PI * 2
    );

    ctx.fillStyle = "#ff4f9a";
    ctx.fill();
}

function gameLoop() {

    let head = {
        x: worm[0].x + dx,
        y: worm[0].y + dy
    };

    if (
        head.x < 0 ||
        head.x >= canvas.width ||
        head.y < 0 ||
        head.y >= canvas.height
    ) {
        restart();
        return;
    }

    for (let part of worm) {
        if (head.x === part.x && head.y === part.y) {
            restart();
            return;
        }
    }

    worm.unshift(head);

    if (head.x === food.x && head.y === food.y) {

        food = {
            x: Math.floor(Math.random() * 20) * size,
            y: Math.floor(Math.random() * 20) * size
        };

    } else {
        worm.pop();
    }

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    drawFood();
    drawWorm();
}

function restart() {

    worm = [
        {x: 200, y: 200},
        {x: 180, y: 200},
        {x: 160, y: 200}
    ];

    dx = size;
    dy = 0;
}

setInterval(gameLoop, 120);

</script>

</body>
</html>
