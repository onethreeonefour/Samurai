<template>
  <div>
    <nav class="menu">
      <div class="menu__item">
        <a class="menu__item-link">Chippin' in</a>
        <img src="../assets/artwork/chippin-in.webp" alt="album" class="menu__item-img" />
        <div class="marquee">
          <span>Chippin' in</span>
          <span>Chippin' in</span>
          <span>Chippin' in</span>
          <span>Chippin' in</span>
        </div>
      </div>
      <div class="menu__item">
        <a class="menu__item-link">Black Dog</a>
        <img src="../assets/artwork/black-dog.webp" alt="album" class="menu__item-img" />
        <div class="marquee">
          <span>Black Dog</span>
          <span>Black Dog</span>
          <span>Black Dog</span>
          <span>Black Dog</span>
        </div>
      </div>
      <div class="menu__item">
        <a class="menu__item-link">A Like Supreme</a>
        <img src="../assets/artwork/a-like-supreme.webp" alt="album" class="menu__item-img" />
        <div class="marquee">
          <span>A Like Supreme</span>
          <span>A Like Supreme</span>
          <span>A Like Supreme</span>
          <span>A Like Supreme</span>
        </div>
      </div>
      <div class="menu__item">
        <a class="menu__item-link">Never Fade Away</a>
        <img src="../assets/artwork/fade-away.webp" alt="album" class="menu__item-img" />
        <div class="marquee">
          <span>Never Fade Away</span>
          <span>Never Fade Away</span>
          <span>Never Fade Away</span>
          <span>Never Fade Away</span>
        </div>
      </div>
    </nav>
  </div>
</template>

<style scoped>
* {
  color: red;
}
.menu__item {
  position: relative;
  padding: 0 6vw;
}
.menu__item-link {
  display: inline-block;
  cursor: pointer;
  position: relative;
  -webkit-text-stroke: 1.5px red;
  -webkit-text-fill-color: transparent;
  color: transparent;
  transition: 0.4s opacity;
}
.menu__item-link::before {
  all: initial;
  counter-increment: menu;
  position: absolute;
  bottom: 60%;
  pointer-events: none;
}
.menu__item-link:hover {
  transition-duration: 0.1s;
  opacity: 0;
}
.menu__item-img {
  pointer-events: none;
  position: absolute;
  height: 50vh;
  max-height: 400px;
  opacity: 0;
  left: 100%;
  top: 50%;
  transform: translate3d(calc(-100%-6vw), -30%, 0) translate3d(0, 20px, 0);
}

.menu__item-link:hover + .menu__item-img {
  opacity: 1;
  transform: translate3d(calc(-100% - 6vw), -30%, 0) rotate3d(0, 0, 1, 4deg);
  transition: all 0.4s;
}

.menu {
  padding: 10vh 0 25vh;
  --offset: 20vw;
  --move-initial: calc(-25% + var(--offset));
  --move-final: calc(-50% + var(--offset));
  font-size: 7vw;
}

.marquee {
  position: absolute;
  top: 0;
  left: 0;
  overflow: hidden;
  color: #fff;
  pointer-events: none;
  mix-blend-mode: difference;
}

.marquee__inner {
  width: fit-content;
  display: flex;
  position: relative;
  animation: marquee 5s linear infinite;
  animation-play-state: paused;
  opacity: 0;
  transition: opacity 0.1s;
}

.menu__item-link:hover ~ .marquee .marquee__inner {
  animation-play-state: running;
  opacity: 1;
  transition-duration: 0.4s;
}

.menu__item-link,
.marquee span {
  white-space: nowrap;
  font-size: 7vw;
  padding: 0 1vw;
  font-weight: 900;
  line-height: 1.15;
}

.marquee span {
  font-style: italic;
}

@keyframes marquee {
  0% {
    transform: translate3d(var(--move-initial), 0, 0);
  }

  100% {
    transform: translate3d(var(--move-final), 0, 0);
  }
}
</style>
