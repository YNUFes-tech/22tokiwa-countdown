<template>
  <!--Copyright (c) 2022 by Francesco Allegrini (https://codepen.io/francesco-allegrini/pen/jeQpaL)-->
  <div class="star comet"></div>
</template>

<script>
const wH = window.innerHeight
const wW = window.innerWidth

const generateStars = n => {
  for (let i = 0; i < n; i++) {
    const div = document.createElement('div')
    div.className = i % 20 == 0 ? 'star star--big' : i % 9 == 0 ? 'star star--medium' : 'star'
    // random everywhere!
    div.setAttribute('style', `top:${Math.round(Math.random() * wH)}px;left:${Math.round(Math.random() * wW)}px;animation-duration:${Math.round(Math.random() * 3000) + 3000}ms;animation-delay:${Math.round(Math.random() * 3000)}ms;`)
    document.body.appendChild(div)
  }
}

generateStars(150)
</script>

<style>
html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  background-color: #03061A;
  position: relative;
  overflow: hidden;
}

.star {
  width: 3px;
  height: 3px;
  border-radius: 50%;
  position: absolute;
  background-color: rgba(237, 205, 163, 0.8);
  box-shadow: 0 0 40px 0 rgba(237, 205, 163, 0.8), 0 0 20px 0 #FFFFFF;
  animation: glow 5s infinite;
}

.star--medium {
  width: 4px;
  height: 4px;
}

.star--big {
  width: 5px;
  height: 5px;
  box-shadow: 0 0 40px 0 #EDCDA3, 0 0 20px 0 #FFFFFF, inset 0 0 4px #FFFFFF;
}

.comet {
  width: 6px;
  height: 6px;
  background-color: rgba(255, 255, 255, 0.6);
  box-shadow: 0 0 40px 0 #EDCDA3, 0 0 20px 0 #FFFFFF, inset 0 0 8px rgba(255, 255, 255, 0.6);
  top: 0;
  left: 80%;
  opacity: 0.3;
  transform: rotate(-45deg) translate(0, -50px);
  animation: comet 6s infinite;
}

.comet:after {
  content: "";
  width: 20vw;
  height: 6px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  box-shadow: 0 0 20px rgba(237, 205, 163, 0.4);
  position: absolute;
  top: 0;
  left: 0;
}

@keyframes glow {
  0% {
    opacity: 0.9;
  }
  50% {
    opacity: 0.2;
  }
  100% {
    opacity: 0.9;
  }
}

@keyframes comet {
  0% {
    transform: rotate(-45deg) translateX(0);
    opacity: 0.3;
  }
  10% {
    opacity: 1;
  }
  20% {
    transform: rotate(-45deg) translateX(-100vw);
    opacity: 0;
  }
  100% {
    transform: rotate(-45deg) translateX(-100vw);
    opacity: 0;
  }
}
</style>