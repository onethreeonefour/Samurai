<template>
  <div class="hero-container">
    <div class="hero-initial-anim">
      <div class="hydra">
        <h1>&lt; System rebooting &gt;</h1>
        <h3>Hydra Ver 2.1 Sys Recovery</h3>
        <h3>Process: {{ progress }}%</h3>
        <div id="progress-bar"></div>
      </div>
    </div>
    <div class="hero-secondary-anim">
      <div class="text-container">
        <div class="glitch anim-text-1" data-text="wake the">wake the&#160;</div>
        <div class="glitch anim-text-1" data-text="fuck up">fuck up,&#160;</div>
        <div class="glitch anim-text-1" data-text="samurai">samurai</div>
        <br />
        <div class="glitch anim-text-2" data-text="we have">we have&#160;</div>
        <div class="glitch anim-text-2" data-text="a city">a city&#160;</div>
        <div class="glitch anim-text-2" data-text="to burn">to burn</div>
      </div>
    </div>
    <div class="hero-final-anim">
      <img src="../assets/Samurai.gif" alt="samurai" class="samurai-image samurai" @load="onImgLoad" />
      <img src="../assets/Samurai-text.png" alt="samurai-txt" class="samurai samurai-text" />
      <div class="cta-container">
        <div class="cta-left">
          <div class="glitch " data-text="fight">fight&#160;</div>
          <div class="glitch" data-text="back">back&#160;</div>
          <div class="glitch" data-text="samurai">samurai&#160;</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { gsap, Power2, Power3 } from "gsap";
export default {
  data() {
    return {
      isLoaded: false,
      progress: 0,
    };
  },
  methods: {
    onImgLoad() {
      this.progressBar();
    },
    progressBar() {
      const el = document.getElementById("progress-bar");
      let width = 1;
      let id = setInterval(() => {
        if (width >= 100) {
          clearInterval(id);
          this.animateIntro();
        } else {
          this.progress++;
          width++;
          el.style.width = width + "%";
        }
      }, 30);
    },
    animateIntro() {
      gsap
        .timeline()
        .to(".hydra", 1.5, {
          autoAlpha: 0,
          display: "none",
          ease: Power2.easeOut,
        })
        .to(".hero-secondary-anim", 0.7, {
          display: "flex",
          ease: Power2.easeIn,
        })
        .from(".anim-text-1", 1.5, {
          autoAlpha: 0,
          y: 100,
          stagger: 0.5,
          ease: Power2.easeOut,
        })
        .from(".anim-text-2", 1.5, {
          autoAlpha: 0,
          y: -100,
          stagger: 0.5,
          ease: Power2.easeOut,
        })
        .to(".text-container", 1.5, {
          delay: 1.25,
          display: "none",
          autoAlpha: 0,
          y: -200,
          stagger: 0.5,
          ease: Power2.easeOut,
        })
        .to(".samurai", 0.25, {
          display: "block",
          ease: Power2.easeIn,
        })
        .from(".samurai", 1.5, {
          autoAlpha: 0,
          y: -100,
          ease: "back",
          stagger: 1.5,
        })
        .to(".cta", 1.5, {
          autoAlpha: 1,
          y: 100,
          ease: Power3.easeOut,
          stagger: 0.5,
        });
    },
  },
};
</script>

<style lang="scss" scoped>
a {
  color: red;
}
#progress-bar {
  margin-top: 1rem;
  width: 1%;
  height: 30px;
  background-color: red;
}
.hero-initial-anim {
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
  color: red;
  text-transform: uppercase;
  .hydra {
    text-align: center;
    border: 4px solid red;
    padding: 3rem 5rem;
    font-family: "Dosis", sans-serif;
    font-size: 1.2rem;
  }
}
.hero-secondary-anim {
  display: none;
  div {
    display: inline-block;
  }
  text-transform: uppercase;
  padding: 2rem;
  font-size: 7vw;
}
.hero-final-anim {
  color: red;
  font-weight: 100;
  text-transform: uppercase;
  img {
    display: none;
    width: 60vw;
    object-fit: cover;
    max-height: 100vh;
    overflow: hidden;
  }
  .samurai-image {
    height: 100vh;
  }
  .samurai-text {
    display: none;
    position: absolute;
    top: 0;
    z-index: 5000;
  }
  .cta-container {
    transition: opacity 0.4s;
    img {
      display: inline;
      width: 400px;
      height: auto;
    }
    .cta {
      opacity: 0;
      font-size: 4vw;
    }
    .cta-left {
      transform: translateY(-50%);
      top: 50%;
      position: absolute;
      left: 2rem;
    }
  }
}

.glitch {
  color: red;
  position: relative;
  margin: 0 auto;
  font-weight: bolder;
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
