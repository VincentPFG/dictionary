<template>
  <v-app dark>
    <!-- <v-main> -->
    <v-carousel v-if="language == 0" height="100%">
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
    <v-carousel v-if="language == 1" height="100%">
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/esfr/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://es.wiktionary.org/wiki/${word}#Etimología`" />
      </v-carousel-item>
    </v-carousel>
    <v-carousel v-if="language == 2" height="100%">
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/fren/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://www.wordreference.com/fres/${word}`" />
      </v-carousel-item>
      <v-carousel-item>
        <iframe :src="`https://fr.wiktionary.org/wiki/${word}`" />
      </v-carousel-item>
    </v-carousel>
    <!-- </v-main> -->
    <v-app-bar

      dense
    >
      <v-spacer />
      <!-- <v-form> -->
      <v-text-field
        v-model="search"
        dense
        outlined
        autofocus
        hide-details
        autocapitalize="none"
        @keyup.enter="({target:{value}})=>word=search"
      >
        <template #append>
          <v-btn icon small @click="({currentTarget})=>{search='';currentTarget.focus();}">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </template>
      </v-text-field>
      <!-- </v-form> -->
      <v-spacer />
      <v-btn-toggle v-model="language" mandatory>
        <v-btn>
          EN
        </v-btn>
        <v-btn>
          ES
        </v-btn>
        <v-btn>
          FR
        </v-btn>
      </v-btn-toggle>
    </v-app-bar>
  </v-app>
</template>

<script>

export default {
  layout: 'empty',
  data () {
    return { word: '', language: [], search: '' }
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
