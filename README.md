# Alarm
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alarm Clock</title>
    <style>
        body {
            margin: 0;
            padding: 0;
        }

        #lebaran {
          font-family: "Lucida Bright", Georgia, serif;
          position: absolute;
          font-size: large;
            padding: 1rem;
            bottom: 60px;
            center: 10px;
            color: #0e3742;
            border-radius: 10px;
        background-color: rgba(255, 255, 255, 0.308);
        }

       
    </style>
</head>
<body>

    <div id="lebaran">“We cannot change the past, but we can change the course of the future by making use of the present.”</div>
    

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Alarm Clock</title>
</head>
<style>
  H3{
    position: absolute;
            padding: 1rem;
            top: 107px;
            center: 10px;
            font-size: large;
            color: #0e3742;
            border-radius: 10px;
        background-color: rgba(255, 255, 255, 0.308);
  }
  
</style>
<body>
  <h3 contenteditable="true">WELCOME TO TKJ 1</h3>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Alarm Clock</title>
</head>
<style>
  h2{
    position: absolute;
            padding: 1rem;
            top: 15px;
            center: 10px;
            font-size: large;
            color: #0e3742;
            border-radius: 10px;
        background-color: rgba(255, 255, 255, 0.308);
  }
  
</style>
<body>
  <h2 contenteditable="true"> SATRIA ABQARI NUGRAHA</h2>
</body>
</html>

<!DOCTYPE html>
<!-- Coding By CodingNepal - youtube.com/codingnepal -->
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Alarm Clock</title>
    <link rel="stylesheet" href="style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <body>
    <div class="wrapper">
      <img src="clock.svg" alt="clock">
      <h1>00:00:00 PM</h1>
      <div class="content">
        <div class="column">
          <select>
            <option value="Hour" selected disabled hidden>Hour</option>
          </select>
        </div>
        <div class="column">
          <select>
            <option value="Minute" selected disabled hidden>Minute</option>
          </select>
        </div>
        <div class="column">
          <select>
            <option value="AM/PM" selected disabled hidden>AM/PM</option>
          </select>
        </div>
      </div>
      <button>Set Alarm</button>
    </div>
    <script src="script.js"></script>
  </body>
</html>
<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
body, .wrapper, .content{
  display: flex;
  align-items: center;
  justify-content: center;
}
body{
  padding: 0 10px;
  min-height: 100vh;
  background: #4A98F7;
}
.wrapper{
  width: 440px;
  padding: 30px 30px 38px;
  background-color: rgba(255, 255, 255, 0.233);
  border-radius: 10px;
  flex-direction: column;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
}
.wrapper img{
  max-width: 103px;
}
.wrapper h1{
  font-size: 38px;
  font-weight: 500;
  margin: 30px 0;
}
.wrapper .content{
  width: 100%;
  justify-content: space-between;
}
.content.disable{
  cursor: no-drop;
}
.content .column{
  padding: 0 10px;
  border-radius: 5px;
  border: 1px solid #ece5e5;
  width: calc(100% / 3 - 5px);
}
.content.disable .column{
  opacity: 0.6;
  pointer-events: none;
}
.column select{
  width: 100%;
  height: 53px;
  border: none;
  outline: none;
  background: none;
  font-size: 19px;
}
.wrapper button{
  width: 100%;
  border: none;
  outline: none;
  color: #fff;
  cursor: pointer;
  font-size: 20px;
  padding: 17px 0;
  margin-top: 20px;
  border-radius: 5px;
  background: #4A98F7;
}
</style>
<script>
const currentTime = document.querySelector("h1"),
content = document.querySelector(".content"),
selectMenu = document.querySelectorAll("select"),
setAlarmBtn = document.querySelector("button");

let alarmTime, isAlarmSet,
ringtone = new Audio("ringtone.mp3");

for (let i = 12; i > 0; i--) {
    i = i < 10 ? `0${i}` : i;
    let option = `<option value="${i}">${i}</option>`;
    selectMenu[0].firstElementChild.insertAdjacentHTML("afterend", option);
}

for (let i = 59; i >= 0; i--) {
    i = i < 10 ? `0${i}` : i;
    let option = `<option value="${i}">${i}</option>`;
    selectMenu[1].firstElementChild.insertAdjacentHTML("afterend", option);
}

for (let i = 2; i > 0; i--) {
    let ampm = i == 1 ? "AM" : "PM";
    let option = `<option value="${ampm}">${ampm}</option>`;
    selectMenu[2].firstElementChild.insertAdjacentHTML("afterend", option);
}

setInterval(() => {
    let date = new Date(),
    h = date.getHours(),
    m = date.getMinutes(),
    s = date.getSeconds(),
    ampm = "AM";
    if(h >= 12) {
        h = h - 12;
        ampm = "PM";
    }
    h = h == 0 ? h = 12 : h;
    h = h < 10 ? "0" + h : h;
    m = m < 10 ? "0" + m : m;
    s = s < 10 ? "0" + s : s;
    currentTime.innerText = `${h}:${m}:${s} ${ampm}`;

    if (alarmTime === `${h}:${m} ${ampm}`) {
        ringtone.play();
        ringtone.loop = true;
    }
});

function setAlarm() {
    if (isAlarmSet) {
        alarmTime = "";
        ringtone.pause();
        content.classList.remove("disable");
        setAlarmBtn.innerText = "Set Alarm";
        return isAlarmSet = false;
    }

    let time = `${selectMenu[0].value}:${selectMenu[1].value} ${selectMenu[2].value}`;
    if (time.includes("Hour") || time.includes("Minute") || time.includes("AM/PM")) {
        return alert("Please, select a valid time to set Alarm!");
    }
    alarmTime = time;
    isAlarmSet = true;
    content.classList.add("disable");
    setAlarmBtn.innerText = "Clear Alarm";
}
setAlarmBtn.addEventListener("click", setAlarm);
</script>
