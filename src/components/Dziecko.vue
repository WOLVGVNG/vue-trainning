<template>
  <div>
    <p>{{ tresc }}</p>
    <br><br>
    Pole tekstowe przekazujące URL do rodzica: <input type='url' v-model='url' @input='sendURL'>
    <button type='button' @click='pasteURL'>Uzupełnij to pole przypadkowym zdjęciem</button>
  </div>
</template>

<script>
export default {
  name: 'Dziecko',
  props: ['tresc'],
  data() {
    return{
      url: '',
    };
  },
  methods: {
    sendURL() {
      this.$emit('url', this.url);
    },
    pasteURL() {
      this.url = 'https://drscdn.500px.org/photo/76092365/m%3D900/v2?webp=true&sig=6ebb197bd0bca92b2992285c273c31123ccd25d97674d8cb6cefa77767bdb575';
      this.$emit('url', this.url);
    },
  },
};
</script>

<style>

</style>
