<template>
  <div id="app" class="container-fluid">

    <div style="width: 640px; margin: 0 auto;">
      <h4>[my-carousel-text-only]</h4>
      <my-carousel-text-only :slideIndex.sync="slideIndex"
                             :showCarousel.sync="showCarousel"/>
    </div>

    <h4>[app]</h4>
    <div>Slide index: {{ slideIndex }}</div>
    <div>Show carousel: {{ showCarousel }}</div>

    <button @click="setSlideIndex(1)" class="btn btn-default mx-2">Set slide index to 1</button>
    <button @click="toggleCarousel" class="btn btn-default mx-2">Toggle carousel</button>

  </div>
</template>

<script>
import Carousel from './components/Carousel.vue'
import CarouselTextOnly from './components/CarouselTextOnly'

export default {
  name: 'app',
  data () {
    return {
      slideIndex: 0,
      showCarousel: true
    }
  },
  methods: {
    setSlideIndex(index) {
      this.slideIndex = index;
    },
    toggleCarousel() {
      this.showCarousel = !this.showCarousel;
    }
  },
  components: {
    MyCarousel: Carousel,
    MyCarouselTextOnly: CarouselTextOnly
  }
}
</script>

<style>

  #app {

    padding: 30px 0;
    font-family: Helvetica, Arial, sans-serif;

    background: repeating-linear-gradient(
      45deg,
      #C5D4E2,
      #C5D4E2 10px,
      #DDD 10px,
      #DDD 20px
    );
  }

</style>
