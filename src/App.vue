<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup


</script>

<script>
import { defineComponent } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger);
export default defineComponent({
  data() {
    return {
      interval: null,
      $text: null,
      texts: ["Pop", "Classic", "Rock", "Jay Zhou", "Shuffle"],
      textIndex: 0,
    }
  },
  mounted() {
    this.initTimer();
    // this.switchText()
    // gsap.to(this.$refs.introImages, {
    //   scrollTrigger: {
    //     trigger: this.$refs.introImages,        
    //   },
    //   y: -150,
    //   scrub: true,
    //   markers: true,
    //   duration: 1,
    // })
    // gsap.to(this.$refs.findImages, {
    //   scrollTrigger: {
    //     trigger: this.$refs.findImages,  
    //     toggleActions: 'restart pause reverse pause'      
    //   },
    //   x: 200,
    //   scrub: true,
    //   markers: true,
    //   ease: 'expo.out',
    //   duration: 1.8,
    // })
  },
  methods: {
    initTimer() {
      clearInterval(this.interval)
      this.interval = setInterval(() => {
        this.switchText()
      }, 1400)
    },
    switchText() {
      const $text = this.$refs.titleSecondLine
      const e = this.textIndex < this.texts.length - 1 ? this.textIndex + 1 : 0;
      gsap.to($text, {
        duration: 0.4,
        yPercent: -10,
        opacity: 0,
        onComplete: () => {
          $text.innerHTML = 'your <span class="title-word">' + this.texts[e] + "</span>?",
            this.textIndex = e,
            gsap.fromTo($text, {
              duration: 0.4,
              opacity: 0,
              yPercent: 10
            }, {
              duration: 0.4,
              opacity: 1,
              yPercent: 0,
              delay: 0
            })
        }
      })
    },
  }
})
</script>

<template>
  <a id="logo" href="https://app.wookmama.co" class="active">
    <svg id="logo-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
      <path
        id="logo-icon-3"
        class="logo-icon-part logo-icon-3"
        d="M16.09,15.94C2.65,9.15,3.57,5.82,4.65,4.72A15.9,15.9,0,0,0,.22,13.31c0,.11,0,.23-.06.35s-.07.45-.09.69h0c0,.25,0,.5-.06.76v.09a1.62,1.62,0,0,0,0,.22C0,17.24.5,18,1.24,18.5h0a2.67,2.67,0,0,0,2.27.25,2.13,2.13,0,0,0,1.1-.93h0A4,4,0,0,1,12,20v8.4C12,30.1,13,32,16.09,32a16,16,0,0,0,11.27-4.74c.88-.9,2.21-4.47-11.27-11.29"
      />
      <path
        id="logo-icon-2"
        class="logo-icon-part logo-icon-2"
        d="M32,16A16,16,0,0,0,16,0,15.82,15.82,0,0,0,8.82,1.7a16,16,0,0,0-4.17,3c-1.08,1.1-2,4.43,11.44,11.22S28.24,26.33,27.36,27.23A15.91,15.91,0,0,0,32,16"
      />
      <path
        id="logo-icon-4"
        class="logo-icon-part logo-icon-4"
        d="M14,26.84c-.7,0-1.35,0-2-.07v1.61C12,30.1,13,32,16.1,32a16,16,0,0,0,7.23-1.78c2.25-1.4-1.56-3.28-9.36-3.35"
      />
      <path
        id="logo-icon-1"
        class="logo-icon-part logo-icon-1"
        d="M18.05,5.13C26.33,5.2,29.14,7.46,31,10.34A16,16,0,0,0,8.82,1.7C6.3,3.11,10.11,5.06,18.05,5.13"
      />
    </svg>
    <span class="logo-text">VPlayer</span>
  </a>
  <div id="main-container">
    <div
      id="page-container-home"
      class="page-container"
      data-node-type="home"
      data-meta-title="Home"
      style="opacity: 1;"
    >
      <section class="page-block home-part" id="intro" data-node-type="intro-block" data-index="0">
        <div class="container part-container">
          <div class="part-text">
            <h1 class="col-sm-offset-1 col-sm-10 part-title">
              好好吃饭，安静听歌
              <span
                ref="titleSecondLine"
                class="title-second-line"
                style="opacity: 0.559841; transform: translate(0%, -4.40159%) translate3d(0px, 0px, 0px);"
              >
                是
                <span class="title-word">interior</span>?
              </span>
            </h1>
          </div>
          <div class="part-images" ref="introImages">
            <div class="part-images-inner part-images-inner-3-images">
              <picture
                class="col-sm-3 part-image"
              >
                <img
                  class="img-responsive part-img part-image-1"
                  src="./assets/list.png"
                  alt="Packaging"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-2"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/lyric.png"
                  alt="Interior"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-3"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/setting.png"
                  alt="Book"
                />
              </picture>
            </div>
          </div>
        </div>
      </section>

      <section
        class="page-block home-part"
        id="find-palettes"
        data-node-type="home-part"
        data-index="1"
      >
        <div class="container part-container">
          <div class="part-text">
            <h2 class="col-sm-offset-1 col-sm-10 part-title">
              Find, create and try
              <span class="title-word">color palettes</span>
            </h2>
            <p
              class="col-sm-offset-2 col-sm-8"
            >Choosing colors for design projects can be a hassle, so we made the color selection process easy, creative and playful!</p>
          </div>
          <div class="part-images">
            <div class="part-images-inner part-images-inner-3-images">
              <picture
                class="col-sm-3 part-image part-image-1"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/next.png"
                  alt="Color palettes"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-2"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Color palettes"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-3"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/lyric.png"
                  alt="Color palettes"
                />
              </picture>
            </div>
          </div>
        </div>
      </section>

      <section
        class="page-block home-part"
        id="preview"
        data-node-type="preview-block"
        data-index="2"
      >
        <div class="container part-container">
          <div class="part-text">
            <h2 class="col-xs-offset-3 col-xs-9 col-sm-offset-3 col-sm-6 part-title">
              Dark & Light
              <span class="title-word">theme</span>
            </h2>
          </div>
          <div class="part-images" ref="findImages">
            <div class="part-images-inner part-images-inner-1-image">
              <picture
                class="col-sm-8 part-image part-image-3"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Color palettes"
                />
              </picture>
            </div>
          </div>
        </div>
      </section>

      <section
        class="page-block home-part"
        id="color-palettes"
        data-node-type="home-part"
        data-index="3"
      >
        <div class="container part-container">
          <div class="part-text">
            <h2 class="col-sm-offset-1 col-sm-10 part-title">
              Hundreds of
              <span class="title-word">songs</span>
            </h2>
          </div>
          <div class="part-images">
            <div class="part-images-inner part-images-inner-3-images">
              <picture
                class="col-sm-3 part-image part-image-1"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/artist.png"
                  alt="Color palettes"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-2"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Color palettes"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-3"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Color palettes"
                />
              </picture>
            </div>
          </div>
        </div>
      </section>

      <section
        class="page-block home-part"
        id="visualizations"
        data-node-type="home-part"
        data-index="4"
      >
        <div class="container part-container">
          <div class="part-text">
            <h2 class="col-sm-offset-1 col-sm-10 part-title">
              High quality
              <span class="title-word">Sound</span>
            </h2>
          </div>
          <div class="part-images">
            <div class="part-images-inner part-images-inner-4-images">
              <picture
                class="col-sm-3 part-image part-image-1"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Visualizations"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-2"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Visualizations"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-3"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Visualizations"
                />
              </picture>
              <picture
                class="col-sm-3 part-image part-image-4"
              >
                <img
                  class="img-responsive part-img"
                  src="./assets/light&dark.png"
                  alt="Visualizations"
                />
              </picture>
            </div>
          </div>
        </div>
      </section>

      <section
        class="page-block home-part"
        id="moodboards"
        data-node-type="home-part"
        data-index="5"
      >
        <div class="container part-container">
          <div class="part-text">
            <h2 class="col-sm-offset-1 col-sm-10 part-title">
              Raise up your
              <span class="title-word">music</span> now!
            </h2>
            <p class="col-sm-offset-1 col-sm-10">
              Free download on the
              <a
                href="https://apps.apple.com/us/app/wookmama-color-visualizer/id1553793793"
                target="_blank"
              >Github</a>, coming soon on direct link donwload.
            </p>
          </div>
        </div>
        <div class="part-footer">
          <a
            href="https://app.termly.io/document/terms-of-use-for-ios-app/2d921f99-7072-4f41-9b64-9c6b114791e2"
            target="_blank"
          >邮箱联系</a> -
          <a
            href="https://app.termly.io/document/privacy-policy/a88846f3-e71d-43c2-b5db-1148d2cef1f5"
            target="_blank"
          >免责声明</a>
          <br />© GuMengYu - 2022 - All rights reserved
        </div>
      </section>

      <footer id="footer">
        <a class="footer-link" href="https://github.com/GuMengYu/v-player" target="_blank">Github</a>
        <a class="footer-link" href="https://github.com/GuMengYu" target="_blank">GuMengYu</a>
      </footer>

      <a
        href="https://apps.apple.com/us/app/wookmama-color-visualizer/id1553793793"
        target="_blank"
        id="download-btn"
      >免费下载 github</a>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Google Sans, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-weight: 700;
}
</style>
