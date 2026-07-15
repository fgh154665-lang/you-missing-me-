# you-missing-me-
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>คิดถึงกันไหม</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:sans-serif;
}

video{
    position:fixed;
    width:100%;
    height:100%;
    object-fit:cover;
    z-index:-1;
    pointer-events:none;
}

.overlay{
    position:fixed;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.5);
}

.container{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    width:320px;
    padding:25px;
    border-radius:20px;
    backdrop-filter: blur(15px);
    background:rgba(255,255,255,0.1);
    text-align:center;
    box-shadow:0 0 30px rgba(0,0,0,0.5);
}

h2{
    margin-bottom:15px;
}

input{
    width:100%;
    padding:10px;
    margin:10px 0;
    border:none;
    border-radius:10px;
}

.buttons{
    display:flex;
    gap:10px;
    margin-top:10px;
}

button{
    flex:1;
    padding:12px;
    border:none;
    border-radius:10px;
    color:white;
    cursor:pointer;
    transition:0.3s;
}

#yes{
    background:linear-gradient(45deg,#ff3b6b,#ff6b81);
}

#no{
    background:gray;
}

.success{
    position:fixed;
    width:100%;
    height:100%;
    background:black;
    display:none;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    color:white;
    font-size:24px;
}
</style>
</head>

<body>

<video autoplay muted loop>
    <source src="video.mp4" type="video/mp4">
</video>

<div class="overlay"></div>

<div class="container">
    <h2>💭 คิดถึงกันไหม 💭</h2>
    <input id="name" placeholder="ชื่อเธอ">

    <div class="buttons">
        <button id="yes" onclick="accept()">💖 ใช่</button>
        <button id="no" onclick="reject()">❌ ไม่</button>
    </div>
</div>

<div id="success" class="success">
    <h1>❤️ ก็รู้อยู่แล้วว่าคิดถึง ❤️</h1>
    <p id="loveText"></p>
</div>

<script>
let yesSize = 1;
let noSize = 1;

function reject(){
    // ปุ่ม "ใช่" ใหญ่ขึ้น
    yesSize += 0.3;
    document.getElementById("yes").style.transform = "scale(" + yesSize + ")";

    // ปุ่ม "ไม่" เล็กลง
    noSize -= 0.2;
    if(noSize < 0.2){
        document.getElementById("no").style.display = "none";
    } else {
        document.getElementById("no").style.transform = "scale(" + noSize + ")";
    }
}

function accept(){
    const name = document.getElementById("name").value || "เธอ";

    document.querySelector(".container").style.display = "none";
    document.getElementById("success").style.display = "flex";

    document.getElementById("loveText").innerHTML =
        "ก็รู้อยู่แล้วว่า " + name + " คิดถึงเรา 😏❤️";

    hearts();
}

/* หัวใจลอย */
function hearts(){
    for(let i=0;i<20;i++){
        let h = document.createElement("div");
        h.innerHTML = "❤️";
        h.style.position = "fixed";
        h.style.left = Math.random()*100 + "vw";
        h.style.bottom = "0px";
        h.style.fontSize = "20px";
        h.style.animation = "float 3s linear";
        document.body.appendChild(h);

        setTimeout(()=>h.remove(),3000);
    }
}
</script>

<style>
@keyframes float{
    0%{transform:translateY(0);}
    100%{transform:translateY(-600px); opacity:0;}
}
</style>

</body>
</html>