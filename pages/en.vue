<template>
  <div>
    <v-carousel height="90vh">
      <v-carousel-item>
        <iframe :src="`https://www.merriam-webster.com/dictionary/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://en.wiktionary.org/wiki/${word}#Pronunciation`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/enfr/${word}`" />
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  asyncData ({ query: { word } }) {
    return { word: word ?? '' }
  }
}
</script>

<style>
iframe {
    border: 0;
    width: 100%;
    height: 100%;
}
body{height: 100%;}
</style>
