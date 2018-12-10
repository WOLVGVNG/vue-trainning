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
      Symulacje: <button type="button" @click='zachod'>Symulacja zachodu</button>
      <button type="button" @click='wschod'>Symulacja wschoodu</button>
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
      zachod() {
         this.$emit('zachod');
      },
      wschod() {
         this.$emit('wschod');
      },
   },
};
</script>

<style>

</style>
