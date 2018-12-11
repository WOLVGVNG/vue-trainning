<template>
   <div>
      Pole przekazujące wartość dziecku: <input type='text' v-model='tresc'>
      <Dziecko :tresc='tresc' @url='getIMG' />
      <img :src='url' alt='obrazek'>
      <div id="cover" :style="{'background-color': 'rgba('+colors.red+','+colors.green+','+colors.blue+','+colors.transparency+')'}"></div>
      <RGB_sliders id='RGB_dziecko' @colors='getColors' />
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
            },
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

   #RGB_dziecko {
      position: absolute;
      left: 250px;
      top: 660px;
   }

   #cover {
      width: 600px;
      height: 400px;
      position: absolute;
      left: 50px;
      top: 200px;
   }

</style>
