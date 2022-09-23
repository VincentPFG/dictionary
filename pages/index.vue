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
        ref="input"
        v-model="search"
        autofocus
        dense
        outlined
        hide-details
        autocapitalize="none"
        clearable
        @keyup.enter="word=search;search=''"
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
  name: 'IndexPage',
  data () {
    return { word: '', language: [], slide: 0, search: '' }
  },
  watch: {
    language () { this.slide = 0 }
  },
  mounted () {
    document.addEventListener('keyup', ({ key, shiftKey }) => {
      if (key === ' ') { this.$refs.input.focus() }

      if (key === 'ArrowLeft') { this.slide-- }
      if (key === 'ArrowRight') { this.slide++ }
      if (key === 'ArrowUp') { this.language-- }
      if (key === 'ArrowDown') { this.language++ }

      if (key === 'Backspace' && shiftKey) { this.search = '' }
    })
  },
  updated () {
    this.$refs.input.focus()

    setTimeout(() => {
      // document.activeElement.blur()
      this.$refs.input.focus()
    }, 2000)
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
