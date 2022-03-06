<script setup>
import { reactive, computed, watchEffect } from 'vue';
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

const author = reactive({
  name: 'hyu',
  books: ['Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery']
})

const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'yes' : 'no'
})

watchEffect()


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
  async mounted() {
    this.initTimer();
    gsap.to(this.$refs.introImages, {
      scrollTrigger: {
        trigger: this.$refs.introImages,
      },
      y: -130,
      scrub: true,
      markers: true,
      duration: 0.8,
    })
  },
  methods: {
    initTimer() {
      clearInterval(this.interval)
      this.interval = setInterval(() => {
        this.switchText()
      }, 2000)
    },
    switchText() {
      const $text = this.$refs.titleSecondLine
      const e = this.textIndex < this.texts.length - 1 ? this.textIndex + 1 : 0;
      gsap.to($text, {
        duration: 0.4,
        yPercent: -10,
        opacity: 0,
        onComplete: () => {
          $text.innerHTML = '<span class="title-word">' + this.texts[e] + "</span>?",
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
    initColorSwitch() {
      setTimeout(() => {
        gsap.from('#preview .part-images', {
          scrollTrigger: {
            trigger: '#preview .part-images',
          },
          x: -200,
          duration: .8,
        })
        gsap.to('body', {
          scrollTrigger: '#intro',
          background: '#F5DEDA',
        })
        gsap.to('body', {
          scrollTrigger: {
            trigger: '#find-palettes',
            toggleActions: 'restart resume reverse pause'
          },
          background: '#E1E4D5',
          duration: 0.5
        })
        gsap.to('body', {
          scrollTrigger: {
            trigger: '#preview',
            toggleActions: 'restart resume reverse pause'
          },
          background: '#A6C2D8',
          duration: 0.5
        })
        gsap.to('body', {
          scrollTrigger: {
            trigger: '#color-palettes',
            toggleActions: 'restart resume reverse pause'
          },
          background: '#E1E2EC',
          duration: 0.5
        })
      }, 200)
    }
  }
})
</script>

<template>
  <a id="logo" href="https://app.wookmama.co" class="active">
    <img src="./assets/logo.png" id="logo-icon" />
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
                喜欢什么呢？
                <span class="title-word"></span>?
              </span>
            </h1>
          </div>
          <div class="part-images" ref="introImages">
            <div class="part-images-inner part-images-inner-3-images">
              <picture class="col-sm-8 part-image">
                <img
                  class="img-responsive part-img part-image-1"
                  src="./assets/首页.png"
                  alt="Packaging"
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
              Recommend songs according to
              <span class="title-word">your taste</span>
            </h2>
            <p
              class="col-sm-offset-2 col-sm-8"
            >Don't know what to listen to? Private FM music gives you the answer</p>
          </div>
          <div class="part-images">
            <div class="part-images-inner part-images-inner-3-images">
              <picture class="col-sm-4 part-image part-image-1">
                <img class="img-responsive part-img" src="./assets/歌手.png" alt="Color palettes" />
              </picture>
              <picture class="col-sm-4 part-image part-image-2">
                <img class="img-responsive part-img" src="./assets/专辑.png" alt="Color palettes" />
              </picture>
              <picture class="col-sm-4 part-image part-image-3">
                <img class="img-responsive part-img" src="./assets/歌单.png" alt="Color palettes" />
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
          <div class="part-images">
            <div class="part-images-inner part-images-inner-1-image">
              <picture class="col-sm-8 part-image part-image-3">
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
              <picture class="col-sm-4 part-image part-image-1">
                <img class="img-responsive part-img" src="./assets/资料库.png" alt="Color palettes" />
              </picture>
              <picture class="col-sm-4 part-image part-image-2">
                <img class="img-responsive part-img" src="./assets/正在播放.png" alt="Color palettes" />
              </picture>
              <picture class="col-sm-4 part-image part-image-3">
                <img class="img-responsive part-img" src="./assets/发现.png" alt="Color palettes" />
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
            <div class="part-images-inner">
              <picture class="col-sm-8 part-image">
                <img class="img-responsive part-img" src="./assets/设置.png" alt="Visualizations" />
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
              Start your
              <span class="title-word">music</span> journey!
            </h2>
            <p class="col-sm-offset-1 col-sm-10">
              Free download on the
              <a
                href="https://github.com/GuMengYu/v-player/releases"
                target="_blank"
              >Github</a>, coming soon on
              <a href="https://github.com/GuMengYu/v-player/releases" target="_blank">direct link</a> donwload.
            </p>
          </div>
        </div>
        <div class="part-footer">
          <a href="mailto:1415515984yuri@gmail.com">邮箱联系</a> -
          <a href="https://github.com/GuMengYu/v-player/blob/dev/LICENSE" target="_blank">LICENSE</a>
          <br />© GuMengYu - 2022 - All rights reserved
        </div>
      </section>
      <a
        href="https://github.com/GuMengYu/v-player/releases"
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
