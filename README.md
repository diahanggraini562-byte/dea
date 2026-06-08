<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<title>Corazón I Love You</title>
<style>
    body{
        margin:0;
        background:#000;
        display:flex;
        justify-content:center;
        align-items:center;
        height:100vh;
        overflow:hidden;
        font-family: Arial, Helvetica, sans-serif;
    }

    #heart{
        position:relative;
        width:600px;
        height:600px;
    }

    .text{
        position:absolute;
        color:#ff4d6d;
        font-size:14px;
        animation: latido 1.5s infinite;
        text-shadow: 0 0 8px #ff4d6d;
        user-select:none;
        white-space:nowrap;
    }

    @keyframes latido{
        0%{transform: scale(1); opacity:0.8;}
        50%{transform: scale(1.2); opacity:1;}
        100%{transform: scale(1); opacity:0.8;}
    }
</style>
</head>
<body>

<div id="heart"></div>

<script>
const heart = document.getElementById("heart");

// Fórmula matemática del corazón
function heartShape(t){
    let x = 16 * Math.pow(Math.sin(t),3);
    let y = 13*Math.cos(t) - 5*Math.cos(2*t) - 2*Math.cos(3*t) - Math.cos(4*t);
    return {x, y};
}

for(let i=0; i<200; i++){
    let t = Math.PI * 2 * Math.random();
    let pos = heartShape(t);

    let span = document.createElement("span");
    span.className = "text";
    span.innerText = "I love you";

    // Escala y centra el corazón
    span.style.left = (pos.x * 15 + 300) + "px";
    span.style.top  = (-pos.y * 15 + 300) + "px";

    heart.appendChild(span);
}
</script>

</body>
</html>
