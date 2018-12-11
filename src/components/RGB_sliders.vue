<template>
   <div>
      R: <input type="range" min='0' max='255' v-model='red' @change='sendColors'>{{ red }}
      <br><br>
      G: <input type="range" min='0' max='255' v-model='green' @change='sendColors'>{{ green }}
      <br><br>
      B: <input type="range" min='0' max='255' v-model='blue' @change='sendColors'>{{ blue }}
      <br><br>
      Transparency: <input type="range" min='0' max='1' step='0.01' v-model='transparency' @change='sendColors'>{{ transparency }}
      <br><br><br>
      Filtry: <button type='button' @click='red = 0, green = 0, blue = 0, transparency = 0, sendColors()'>Clear</button>
      <button type='button' @click='red = 0, green = 0, blue = 48, transparency = 0.3, sendColors()'>Beautiful</button>
      <button type='button' @click='red = 137, green = 146, blue = 0, transparency = 0.14, sendColors()'>Old</button>
      <br><br>
      Symulacje: <button type="button" @click='simulation(1)'>Symulacja zachodu</button>
      <button type="button" @click='simulation(0)'>Symulacja wschodu</button>
   </div>
</template>

<script>
let th = this;

export default {
   name: 'RGB_sliders',
   data() {
      return {
         red: 0,
         green: 0,
         blue: 0,
         transparency: 0,
      };
   },
   methods: {
      sendColors() {
         this.$emit('colors', [this.red, this.green, this.blue, this.transparency]);
      },
      simulation(a) {
         let mylet;
         let th = this;

         if(a==1) {
            mylet = setInterval(darkening, 1)

         
            function darkening() {
               if(th.transparency<=0.9) {
                  th.$emit('colors', [th.red, th.green, th.blue, th.transparency]);
                  th.transparency = th.transparency + 0.001;
               } else {
                  clearInterval(mylet);
                  th.transparency = 0.9;
                  th.$emit('colors', [th.red, th.green, th.blue, th.transparency]);
               }
            }
         }
         else if (a == 0) {
             mylet = setInterval(brightening, 1)

            function brightening() {
               if(th.transparency>=0) {
                  th.$emit('colors', [th.red, th.green, th.blue, th.transparency]);
                  th.transparency = th.transparency - 0.001;
               } else {
                  clearInterval(mylet);
                  th.transparency = 0;
                  th.$emit('colors', [th.red, th.green, th.blue, th.transparency]);
               }
            }
         }
      },
   },
};
</script>

<style>

</style>
