<template>
  <v-app dark>
    <v-carousel v-if="language == 0" v-model="slide" height="100%">
      <v-carousel-item>
        <iframe :src="`https://www.merriam-webster.com/dictionary/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/enfr/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/enes/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://en.wiktionary.org/wiki/${word}#Pronunciation`" />
      </v-carousel-item>
    </v-carousel>
    <v-carousel v-if="language == 1" v-model="slide" height="100%">
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/esfr/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/esen/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/conj/esverbs.aspx?v=${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://es.wiktionary.org/wiki/${word}#Etimología`" />
      </v-carousel-item>
    </v-carousel>
    <v-carousel v-if="language == 2" v-model="slide" height="100%">
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/fren/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/fres/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/conj/frverbs.aspx?v=${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://fr.wiktionary.org/wiki/${word}`" />
      </v-carousel-item>
    </v-carousel>
    <v-app-bar dense>
      <v-spacer />
      <v-text-field
        dense
        outlined
        hide-details
        autocapitalize="none"
        clearable
        @keyup.enter="({target})=>{word=target.value;slide=0;target.blur()}"
      />
      <v-spacer />
      <v-btn-toggle v-model="language" mandatory>
        <v-btn v-for="lang in ['EN','ES','FR']" :key="lang" @click="slide=0">
          {{ lang }}
        </v-btn>
      </v-btn-toggle>
    </v-app-bar>
  </v-app>
</template>

<script>

export default {
  data () {
    return { word: '', language: [], slide: 0 }
  }
}
</script>

<style>
iframe {
  border: 0;
  width: 100%;
  height: 100%;
}

body {
  height: 100%;
}
</style>
