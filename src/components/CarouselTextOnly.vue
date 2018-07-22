<template>

  <div v-show="showCarousel" class="carousel-container">

    <div class="carousel-close">
      <button @click="closeCarousel" type="button" aria-label="Close" class="close">×</button>
    </div>

    <b-carousel id="carousel1"
                controls
                background="rgba(255, 255, 255, .75)"
                style="opacity: 0.75"
                img-width="640"
                img-height="150"
                v-model="internalSlideIndex"
                :interval="0"
    >

      <b-carousel-slide img-blank>
        <div class="heading">Bookmark 1 at 00:00:15</div>
        <div class="summary">Ian Craig added a bookmark on 20th June 2018 - 09:30:15</div>
        <div class="text">If you look closely you can see the man in the red jacket take something from his left pocket and then throw it into the bushes</div>
      </b-carousel-slide>

      <b-carousel-slide img-blank>
        <div class="heading">Bookmark 2 at 00:00:20</div>
        <div class="summary">Mike Smith added a bookmark on 20th June 2018 - 09:30:15</div>
        <div class="text">If you look closely you can see the man in the red jacket take something from his left pocket and then throw it into the bushes</div>
      </b-carousel-slide>

      <b-carousel-slide img-blank>
          <div class="heading">.heading</div>
          <div class="summary">.summary</div>
          <div class="text">.text</div>
      </b-carousel-slide>

    </b-carousel>

    <p>
      Internal slide index: {{ internalSlideIndex }}<br>
    </p>

  </div>
</template>

<script>
  export default {
    props: {
      slideIndex: Number,
      showCarousel: Boolean,
    },
    data() {
      return {
        internalSlideIndex: 0,
      }
    },
    watch: {
      slideIndex(newSlideIndex) {
        this.internalSlideIndex = newSlideIndex;
      },
      internalSlideIndex(newInternalSlideIndex) {
        this.$emit('update:slideIndex', newInternalSlideIndex)
      }
    },
    methods: {
      closeCarousel() {
        this.$emit('update:showCarousel', false)
      }
    }
  }
</script>

<style>

  .carousel-container {
    position: relative
  }

  .carousel-close {
    position: absolute;
    top: 5px;
    right: 22px;
    z-index: 1;
  }

  .carousel-close {
    font-size: 1.75em /* Make the icon bigger */
  }

  /* The specificity of including .carousel in the selector is required */

  .carousel .carousel-caption {
    top: 0; /* Position at the top of the carousel rather than the bottom */
    left: 8%; /* Reduce from 15% */
    right: 8%;
    padding: 12px 0; /* Tighten up the top and bottom padding from the default of 20px; */
    text-align: initial;
    color: #212529;
  }

  .carousel .carousel-control-prev,
  .carousel .carousel-control-next{
    width: 8% /* Reduce from 15% */
  }

  /* Override the svg image size and colour */
  .carousel .carousel-control-prev-icon,
  .carousel .carousel-control-next-icon {
    width: 25px; /* increased from 20px */
    height: 25px;
    color: #7F887E;
  }

  .carousel .carousel-control-prev-icon {
    background-image: url("data:image/svg+xml;charset=utf8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%555B55' viewBox='0 0 8 8'%3E%3Cpath d='M5.25 0l-4 4 4 4 1.5-1.5-2.5-2.5 2.5-2.5-1.5-1.5z'/%3E%3C/svg%3E");
  }

  .carousel .carousel-control-next-icon {
    background-image: url("data:image/svg+xml;charset=utf8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%555B55' viewBox='0 0 8 8'%3E%3Cpath d='M1.5 0l-1.5 1.5 2.5 2.5-2.5 2.5 1.5 1.5 4-4-4-4z'/%3E%3C/svg%3E");
  }

  .carousel .heading {
    font-size: 1.125em;
    font-weight: bold;
  }

  .carousel .summary {
    margin-bottom: 10px;
    font-weight: bold;
  }

</style>
