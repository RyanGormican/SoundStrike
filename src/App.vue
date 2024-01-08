<template>
  <div id="app">
    <div class="container">
      <div id="myCarousel" class="carousel slide" data-ride="carousel">
        <div class="carousel-inner">
          <div v-for="(item, index) in items" :key="index" :class="{ 'carousel-item': true, active: index === 0 }">
            <div class="row">
              <div v-for="(letter, letterIndex) in ['a', 'b', 'c', 'd']" :key="letterIndex" class="col-md-6" @click="speakItem(items[(index * 4 + letterIndex) % items.length])">
                <h3>{{ items[(index * 4 + letterIndex) % items.length].title }}</h3>
                <iconify-icon :icon="items[(index * 4 + letterIndex) % items.length].icon" :inline="false" height="50vh"/>
              </div>
            </div>
          </div>
        </div>
        <a class="carousel-control-prev" href="#myCarousel" role="button" data-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="sr-only">Previous</span>
        </a>
        <a class="carousel-control-next" href="#myCarousel" role="button" data-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="sr-only">Next</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css';
import 'bootstrap/dist/js/bootstrap.bundle.min.js';
import { Icon } from '@iconify/vue';

export default {
  name: 'App',
  components: {
    IconifyIcon: Icon,
  },
  data() {
    return {
      items: [
        { title: 'Cow', icon: 'mdi:cow' },
        { title: 'Fish', icon: 'mdi:fish' },
        { title: 'Chicken', icon: 'fluent-emoji-high-contrast:chicken' },
        { title: 'Tree', icon: 'mdi:tree' },
        { title: 'Item 5', icon: 'mdi:text' },
        { title: 'Item 6', icon: 'mdi:text' },
        { title: 'Item 7', icon: 'mdi:text' },
        { title: 'Item 8', icon: 'mdi:text' },
      ],
    };
  },
   methods: {
    async speakItem(item) {
      await this.speak(item.title);
      for (const letter of item.title) {
        await this.speak(letter);
      }
      await this.speak(item.title)
    },

    speak(text) {
      return new Promise((resolve) => {
        const synthesis = window.speechSynthesis;
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'en-US';
        utterance.onend = resolve;
        synthesis.speak(utterance);
      });
    },
  },
};
</script>

<style>
#app {
  overflow: hidden;
  background-color: lightblue;
  min-height: 100vh;
}
</style>