<script>
export default {
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.$nextTick(() => {
        this.setBodyScrollStyle();
      });
    },
    setBodyScrollStyle() {
      document.body.style.setProperty("--scrollTop", `${window.scrollY}px`);
    },
  },
};
</script>

<template>
  <header class="main-header">
    <div class="layers">
      <div class="layer__header">
        <div class="layer__caption">Welcome to Vue</div>
        <div class="layer__title">Fairy forest</div>
      </div>

      <div class="layer layers__base"></div>

      <div class="layer layers__middle"></div>

      <div class="layer layers__front"></div>
    </div>
  </header>

  <article class="main-article">
    <div class="main-article__content">
      <h2 class="main-article__header">To be continued</h2>
      <p class="main-article__text">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis,
        adipisci quam! Asperiores doloribus est provident, corporis ut saepe,
        deserunt eligendi voluptatibus, animi temporibus fugit iure! Quas vel at
        corrupti atque minima quam.
      </p>

      <div class="copyright">©Cloudmenson</div>
    </div>
  </article>
</template>

<style>
@import "@/styles/variables.css";

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

@font-face {
  font-family: raleway_f;
  src: url(./fonts/raleway-regular.woff2);
}

@font-face {
  font-family: raleway_f;
  src: url(./fonts/raleway-black.woff2);
  font-weight: 900;
}

body {
  background-color: #010101;
  line-height: 1.55;
  font-family: raleway_f;
}

.main-header {
  position: relative;
}

.layers {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  overflow: hidden;
}

.layer__header {
  margin-top: calc(var(--index) * -0.8);
  text-transform: uppercase;
  font-weight: 900;
  color: hsla(55, 100%, 98%, 0.894);
  text-shadow: 0 0 15px #ded375f3;
  transform: translate3d(0, calc(var(--scrollTop) / 2), 0);
  will-change: transform;
  z-index: 1;
}

.layer__caption {
  font-size: calc(var(--index) / 1.5);
  letter-spacing: calc(var(--index) / 3.5);
}

.layer__title {
  font-size: calc(var(--index) * 2.5);
  letter-spacing: calc(var(--index) / 2.5);
}

.layer {
  position: absolute;
  background-size: cover;
  background-position: center;
  width: 100%;
  height: 100%;
  will-change: transform;
  z-index: 2;
}

.layers__base {
  background-image: url(./assets/img/layer-base.png);
  transform: translate3d(0, calc(var(--scrollTop) / 1.5), 0);
  z-index: 0;
}

.layers__middle {
  background-image: url(./assets/img/layer-middle.png);
  transform: translate3d(0, calc(var(--scrollTop) / 2.5), 0);
}

.layers__front {
  background-image: url(./assets/img/layer-front.png);
  transform: translate3d(0, calc(var(--scrollTop) / 5.5), 0);
}

.main-article {
  min-height: 100vh;
  background-image: url(./assets/img/dungeon.jpg);
}
</style>
