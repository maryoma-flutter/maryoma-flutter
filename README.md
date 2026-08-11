<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pink Cat</title><style>
    body {
        margin: 0;
        height: 100vh;
        background: white;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .name {
        font-family: Georgia, serif;
        font-size: 35px;
        color: #8FD3FF;
        margin-bottom: 30px;
    }

    .cat {
        color: #ff8fc7;
        font-family: monospace;
        font-size: 28px;
        line-height: 1.1;
        white-space: pre;
        text-align: center;
    }
</style>

</head><body><div class="name" id="name"></div><pre class="cat" id="cat"></pre><script>

const name = "Hi, I'm Maryam Hisham";

const cat = `
        /\\_/\\\\
       ( o.o )
        > ^ <
     /         \\
    /           \\
   /_____________\\
      ||     ||
      ||     ||
`;

let n = 0;
let i = 0;

function writeName() {
    if (n < name.length) {
        document.getElementById("name").textContent += name[n];
        n++;
        setTimeout(writeName, 100);
    } else {
        drawCat();
    }
}

function drawCat() {
    if (i < cat.length) {
        document.getElementById("cat").textContent += cat[i];
        i++;
        setTimeout(drawCat, 50);
    }
}

writeName();

</script></body>
</html>
