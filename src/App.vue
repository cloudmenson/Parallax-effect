<script>
// import { gsap } from "gsap";
// import { ScrollTrigger } from "gsap/ScrollTrigger";
// import scrollSmooth from "scroll-smooth";

export default {
  mounted() {
    // gsap.registerPlugin(ScrollTrigger, scrollSmooth);
    // scrollSmooth.create({
    //   wrapper: ".wrapper",
    //   content: ".content",
    // });

    // console.log(window.gsap);

    if (typeof window !== "undefined") {
      window.addEventListener("scroll", this.handleScroll);
    }
  },
  beforeUnmounted() {
    if (typeof window !== "undefined") {
      window.removeEventListener("scroll", this.handleScroll);
    }
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
  <div class="wrapper">
    <div class="content">
      <header class="main-header">
        <div class="layers">
          <div class="layer__header">
            <div class="layer__caption">Welcome to Vue</div>
            <div class="layer__title">Fairy forest</div>
          </div>

          <div class="layer layers__base" />

          <div class="layer layers__middle" />

          <div class="layer layers__front" />
        </div>
      </header>

      <article class="main-article">
        <div class="main-article__content">
          <h2 class="main-article__header">To be continued</h2>
          <p class="main-article__text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit.
            Perferendis, adipisci quam! Asperiores doloribus est provident,
            corporis ut saepe, deserunt eligendi voluptatibus, animi temporibus
            fugit iure! Quas vel at corrupti atque minima quam.
          </p>
        </div>
        <div class="copyright">©Cloudmenson</div>
      </article>
    </div>
  </div>
</template>

<style src="@/App.css" />
