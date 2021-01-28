<template>
  <div class="store-container">
    <video src="../assets/store/glitch.mp4" autoplay loop></video>
    <a href="https://us.gear.cdprojektred.com/game/cyberpunk-2077.html"
      ><img src="../assets/Samurai.png" alt="samurai" class="chromatic"
    /></a>
    <svg width="0" height="0">
      <filter id="chromatic">
        <feColorMatrix
          type="matrix"
          result="red_"
          values="4 0 0 0 0
              0 0 0 0 0 
              0 0 0 0 0 
              0 0 0 1 0"
        />
        <feOffset in="red_" dx="2" dy="0" result="red" />
        <feColorMatrix
          type="matrix"
          in="SourceGraphic"
          result="blue_"
          values="0 0 0 0 0
              0 3 0 0 0 
              0 0 10 0 0 
              0 0 0 1 0"
        />
        <feOffset in="blue_" dx="-10" dy="5" result="blue" />
        <feBlend mode="screen" in="red" in2="blue" />
      </filter>
    </svg>
    <div class="glitch" data-text="show your support ">Show your support</div>
  </div>
</template>
<script>
export default {};
</script>

<style lang="scss" scoped>
.store-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  video {
    position: absolute;
    width: 100%;
  }
  img {
    height: 100vh;
    z-index: 100;
    mix-blend-mode: difference;
  }
  div {
    position: absolute;
    z-index: 100;
    bottom: 0;
    font-size: 4vw;
    mix-blend-mode: difference;
  }
}
img:hover {
  animation: shake 0.7s;
  animation-iteration-count: infinite;
}
img.chromatic {
  /* When the animation is finished, start again */

  position: relative;
  -webkit-filter: url(#chromatic);
}

@keyframes shake {
  0% {
    -webkit-transform: translate(2px, 1px) rotate(0deg);
  }
  10% {
    -webkit-transform: translate(-1px, -2px) rotate(-1deg);
  }
  20% {
    -webkit-transform: translate(-3px, 0px) rotate(1deg);
  }
  30% {
    -webkit-transform: translate(0px, 2px) rotate(0deg);
  }
  40% {
    -webkit-transform: translate(1px, -1px) rotate(1deg);
  }
  50% {
    -webkit-transform: translate(-1px, 2px) rotate(-1deg);
  }
  60% {
    -webkit-transform: translate(-3px, 1px) rotate(0deg);
  }
  70% {
    -webkit-transform: translate(2px, 1px) rotate(-1deg);
  }
  80% {
    -webkit-transform: translate(-1px, -1px) rotate(1deg);
  }
  90% {
    -webkit-transform: translate(2px, 2px) rotate(0deg);
  }
  100% {
    -webkit-transform: translate(1px, -2px) rotate(-1deg);
  }
}
.glitch {
  text-transform: uppercase;
  color: red;
  position: relative;
  margin: 0 auto;
  font-weight: bolder;
  mix-blend-mode: difference;
}

@keyframes noise-anim {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
    }
  }
}
.glitch:after {
  content: attr(data-text);
  position: absolute;
  left: 2px;
  text-shadow: -2px 0 rgb(0, 255, 0);
  top: 0;
  color: red;
  background: black;
  overflow: hidden;
  clip: rect(0, 900px, 0, 0);
  animation: noise-anim 2s infinite linear alternate-reverse;
}

@keyframes noise-anim-2 {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
    }
  }
}
.glitch:before {
  content: attr(data-text);
  position: absolute;
  left: -2px;
  text-shadow: 2px 0 blue;
  top: 0;
  color: red;
  background: black;
  overflow: hidden;
  clip: rect(0, 900px, 0, 0);
  animation: noise-anim-2 3s infinite linear alternate-reverse;
}
</style>
