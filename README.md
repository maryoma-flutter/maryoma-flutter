<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Playfair+Display&size=35&pause=1000&color=8FD3FF&center=true&vCenter=true&width=700&lines=Hi,+I'm+Maryam+Hisham" />
</p>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Pink Cat</title>

    <style>
        body {
            margin: 0;
            height: 100vh;
            background: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
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
</head>

<body>

<pre class="cat" id="cat"></pre>

<script>
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

let i = 0;

function drawCat() {
    if (i < cat.length) {
        document.getElementById("cat").textContent += cat[i];
        i++;
        setTimeout(drawCat, 70);
    }
}

drawCat();
</script>

</body>
</html>
