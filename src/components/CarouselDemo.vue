<template>
  <div class="CarouselDemo">
    <h1>CarouselDemo</h1>
    <div class="CarouselDemo_carousel">
      <button
        @click="slideLeft"
        class="CarouselDemo_btn CarouselDemo_btn-left"
        type="button"
      >
        <i class="icon-arrow-left"></i>
      </button>
      <Carousel
        class="CarouselDemo_slider"
        :loop="config.loop"
        ref="slider"
        :navigate-to="config.navigateTo"
        :per-page="config.perPage"
        :per-page-custom="config.perPageCustom"
        :scroll-per-page="config.scrollPerPage"
        :navigation-enabled="config.navigationEnabled"
        :pagination-enabled="config.paginationEnabled"
      >
        <Slide
          class="CarouselDemo_slide"
          v-for="item in carouselData"
          :key="item.id"
        >
          <a
            class="CarouselDemo_userpic"
            href="#"
          >
            <img
              class="CarouselDemo_userpicImg"
              :src="item.img"
              :alt="`Image for ${item.text}`"
            >
            {{item.text}}
          </a>
          <button
            class="CarouselDemo_deleteBtn"
            type="button"
            name="button"
            :click="onDelete"
          >
            <i class="icon-close"></i>
          </button>
        </Slide>
      </Carousel>
      <button
        @click="slideRight"
        class="CarouselDemo_btn CarouselDemo_btn-right"
        type="button"
      >
        <i class="icon-arrow-right"></i>
      </button>
    </div>
  </div>
</template>

<script>
import carouselData from './../mocked-data/carouselData'
import {Carousel, Slide} from 'vue-carousel'

export default {
  name: 'CarouselDemo',
  components: {
    Carousel,
    Slide
  },
  data () {
    return {
      carouselData,
      config: {
        loop: true,
        navigateTo: 0,
        perPage: 1,
        perPageCustom: [[576, 4], [992, 8]],
        scrollPerPage: true,
        navigationEnabled: false,
        paginationEnabled: false
      },
    }
  },
  methods: {
    slideLeft () {
      this.config.navigateTo = this.$refs.slider.getPreviousPage()
    },
    slideRight () {
      this.config.navigateTo = this.$refs.slider.getNextPage()
    },
    onDelete () {
      console.info('onDelete')
    },
  },
}
</script>

<style scoped>
  @import "./../styles/fonts.css";
  @import "./../styles/icons.css";

  .CarouselDemo_carousel {
    display: flex
  }

  .CarouselDemo_btn {
    padding-top: 1.375rem;
    font-size: 3.1875rem;
    color: #f00;
    background-color: #fff;
  }

  .CarouselDemo_btn:hover,
  .CarouselDemo_btn:focus,
  .CarouselDemo_btn:active {
    color: gray
  }

  .CarouselDemo_btn-left,
  .CarouselDemo_btn-right {
    margin: auto 0
  }

  .CarouselDemo_btn-left {
    padding-left: 0
  }

  .CarouselDemo_btn-right {
    padding-right: 0
  }

  .CarouselDemo_slide {
    position: relative
  }

  .CarouselDemo_userpic {
    max-width: 7.5rem;
    display: flex;
    flex-direction: column;
    align-content: center;
    background: transparent;
    text-align: center;
    font-size: .8125rem;
    color: #676767;
    line-height: 1.0625rem;
    text-transform: none;
    font-family: "Frutiger LT Std";
    margin: auto;
  }

  .CarouselDemo_userpic:hover,
  .CarouselDemo_userpic:active,
  .CarouselDemo_userpic:focus {
    text-decoration: none;
    color: darkblue;
  }

  .CarouselDemo_userpicImg {
    max-width: 7.5rem;
    display: flex;
    flex-direction: column;
    align-content: center;
    width: 3.875rem;
    height: 3.875rem;
    margin: auto auto 0.4375rem;
  }

  .CarouselDemo_deleteBtn {
    font-size: 0.5625rem;
    line-height: 0.5625rem;
    padding: 0.40625rem;
    letter-spacing: 0;
    width: 0.5625rem;
    height: 0.5625rem;
    box-sizing: content-box;
    position: absolute;
    background-color: #fff;
    top: 2.875rem;
    left: 50%;
    margin-left: 0.875rem;
    z-index: 4;
  }
</style>

