<script>

export default {
  data() {
    return {
      slides: [
        {id: 0, title: "Title slide #1", img: "src/assets/img/1.jpg"},
        {id: 1, title: "Title slide #2", img: "src/assets/img/2.jpg"},
        {id: 2, title: "Title slide #3", img: "src/assets/img/3.jpg"},
        {id: 3, title: "Title slide #4", img: "src/assets/img/4.jpg"},
        {id: 4, title: "Title slide #1", img: "src/assets/img/1.jpg"},
      ],
      
      current: 0
    }
  },
  methods: {
    setSlide(id) {
      this.current = id
    },
    move(type) {
      switch(type) {
        case(0):
          if(this.current-1 >= 0)
            this.current -= 1
          break
        case(1):
          if(this.current+1 <= this.slides.length-1)
            this.current += 1
          break;
      }
    }
  }
  ,
}

</script>

<template>

<div class="container">
  <div class="vue-slider-title">
    <span>Vue Simple Slider. Author: <a href="https://github.com/VladimirKostikov">Vladimir Kostikov</a></span>
  </div>
  <div class="vue-slider-main">
    <div class="vue-slider-slides">
      <div class="vue-slider-slide" v-for="slide in slides"><img class="animate__animated animate__fadeIn" v-if="slide.id == current" :src="slide.img" :alt="slide.title"></div>
    </div>
    <div class="vue-slider-arrows">
      <div class="vue-slider-arrow" @click="move(0)"><img src="src/assets/arrow.png" alt=""></div>
      <div class="vue-slider-arrow" @click="move(1)"><img src="src/assets/arrow.png" alt=""></div>
    </div>
    <div class="vue-slider-controllers">
      <div class="vue-slider-controllers-main">
        <div class="vue-slider-controller" v-for="(slide, index) in slides" @click="setSlide(slide.id)">
          <div class="vue-slider-controller-full" :class="{active: current == slide.id}"></div>
        </div>
      </div>
    </div>
  </div>
</div>

</template>