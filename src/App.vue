<template>
  <div>
    Pole przekazujące wartość dziecku: <input type='text' v-model='tresc'>
    <Dziecko :tresc='tresc' @url='getIMG'/>
    <img :src='url' alt='obrazek'>
    <div id="cover" :style="{'background-color': 'rgba('+colors.red+','+colors.green+','+colors.blue+','+colors.transparency+')'}"></div>
    <RGB_sliders id='RGB_dziecko' @colors='getColors' @zachod='handleZachod' @wschod='handleWschod'/>
  </div>
</template>

<script>
import Dziecko from '@/components/Dziecko.vue';
import RGB_sliders from '@/components/RGB_sliders.vue';

export default {
  name: 'App',
  data() {
    return {
      tresc: '',
      url: '',
      colors: {
        red: 0,
        green: 0,
        blue: 0,
        transparency: 0,
      }
    };
  },
  components: {
    Dziecko,
    RGB_sliders,
  },
  methods: {
    getIMG(value) {
      this.url = value;
    },

    getColors(value) {
      this.colors.red = value[0];
      this.colors.green = value[1];
      this.colors.blue = value[2];
      this.colors.transparency = value[3];
    },

    handleZachod() {
      let mylet;
      let a = 0;
      let th = this;

      mylet = setInterval(sciemnianie, 1)

      function sciemnianie() {
        if(th.colors.transparency < 0.9) {
          th.colors.transparency = th.colors.transparency + 0.0005;
          console.log(th.colors.transparency)
        }
        else {
          clearInterval(mylet);
        }
      }
    },
    handleWschod() {
      let mylet;
      let a = 0;
      let th = this;

      mylet = setInterval(zjasnianie, 1)

      function zjasnianie() {
        if(th.colors.transparency > 0) {
          th.colors.transparency = th.colors.transparency - 0.0005;
          console.log(th.colors.transparency);
        }
        else {
          clearInterval(mylet);
        }
      }
    },
  },
};
</script>

<style>
  img {
    width: 600px;
    height: 400px;
    position: absolute;
    left: 50px;
    top: 200px;
  }

  #RGB_dziecko{
    position: absolute;
    left: 250px;
    top: 660px;
  }

  #cover{
    width: 600px;
    height: 400px;
    position: absolute;
    left: 50px;
    top: 200px;
  }
</style>
