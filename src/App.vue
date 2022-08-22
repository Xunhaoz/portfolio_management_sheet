<template>
  <v-app>
    <v-app-bar
      app
      color="grey-blue"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Walnutek Logo"
          class="shrink mr-2"
          contain
          src="https://www.walnutek.com/img/logo.74c6d88e.png"
          transition="scale-transition"
          width="140"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://www.walnutek.com/"
        target="_blank"
        text
      >
        <span class="mr-2">官方網站</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main >
      <ExplaneDemonstration/>
      <AnswerQuestionary/>
    </v-main>
    
    <v-footer
      color="blue-grey lighten-1"
      bottom
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
        <v-btn
          v-for="link in links"
          :key="link[0]"
          color="white"
          text
          rounded
          class="my-2"
          :href="link[1]"
        >
          {{ link[0] }}
        </v-btn>
        <v-col
          class="blue-grey lighten-2 py-4 text-center white--text"
          cols="12"
        >
          © Copyright 2019 - {{ new Date().getFullYear() }} — <strong>Walnutek Technology Co., Ltd.</strong> Rights Reserved
        </v-col>
      </v-row>
    </v-footer>
    <v-space></v-space>
  </v-app>
</template>

<script>
import ExplaneDemonstration from './components/ExplaneDemonstration.vue'
import AnswerQuestionary from './components/AnswerQuestionary.vue';

export default {
  name: 'App',

  components: {
    ExplaneDemonstration,
    AnswerQuestionary,
  },

  data: () => ({
    links: [
        ['官方網站', "https://www.walnutek.com/"],
        ['關於我們', "https://www.walnutek.com/about/"],
        ['成功案例', "https://www.walnutek.com/service/"],
        ['聯絡我們', "https://www.walnutek.com/contact/"],
    ],
  }),
};
</script>
