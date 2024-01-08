<template>
  <div id="app">
    <div class="container">
      <div id="myCarousel" class="carousel slide" data-ride="carousel">
        <div class="carousel-inner">
          <div v-for="(item, index) in items" :key="index" :class="{ 'carousel-item': true, active: index === 0 }">
            <div class="row">
              <div v-for="(letter, letterIndex) in ['a', 'b', 'c', 'd']" :key="letterIndex" class="col-md-6" @click="speakItem(items[(index * 4 + letterIndex) % items.length])">
                <h3>{{ items[(index * 4 + letterIndex) % items.length].title }}</h3>
                <iconify-icon :icon="items[(index * 4 + letterIndex) % items.length].icon" :inline="false" height="45vh"/>
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
  { title: 'Acorn', icon: 'fxemoji:acorn'},
  { title: 'Ant', icon: 'noto-v1:ant'},
  { title: 'Apple', icon: 'noto:red-apple'},
  { title: 'Arm', icon: 'fluent-emoji:mechanical-arm'},
  { title: 'Ball', icon: 'emojione:soccer-ball' },
  { title: 'Banana', icon: 'twemoji:banana' },
  { title: 'Bed', icon: 'twemoji:bed' },
  { title: 'Blue', icon: 'twemoji:blue-heart' },
  { title: 'Bird', icon: 'twemoji:bird' },
  { title: 'Bus', icon: 'fluent-emoji-flat:bus' },
  { title: 'Cake', icon: 'noto-v1:birthday-cake' },
  { title: 'Car', icon: 'icon-park:car' },
  { title: 'Cow', icon: 'twemoji:cow-face' },
  { title: 'Chicken', icon: 'emojione:chicken' },
  { title: 'Dog', icon: 'noto:dog' },
  { title: 'Dolphin', icon: 'twemoji:dolphin' },
  { title: 'Drum', icon: 'noto:drum' },
  { title: 'Duck', icon: 'twemoji:duck' },
  { title: 'Ear', icon: 'twemoji:ear' },
  { title: 'Egg', icon: 'twemoji:egg' },
  { title: 'Elephant', icon: 'twemoji:elephant' },
  { title: 'Eye', icon: 'twemoji:eye' },
  { title: 'Fire', icon: 'twemoji:fire' },
  { title: 'Fish', icon: 'twemoji:fish' },
  { title: 'Flower', icon: 'twemoji:hibiscus' },
  { title: 'Frog', icon: 'twemoji:frog' },
  { title: 'Goat', icon: 'twemoji:goat' },
  { title: 'Gorilla', icon: 'twemoji:gorilla' },
  { title: 'Grapes', icon: 'twemoji:grapes' },
  { title: 'Green', icon: 'twemoji:green-heart' },
  { title: 'Guitar', icon: 'twemoji:guitar' },
  { title: 'Hat', icon:   'emojione-v1:top-hat' },
  { title: 'Heart', icon: 'fluent-emoji-flat:red-heart' },
  { title: 'Horse', icon: 'twemoji:horse' },
  { title: 'House', icon: 'twemoji:house' },
  { title: 'Ice', icon: 'noto:ice' },
  { title: 'Ice Cream', icon: 'fluent-emoji-flat:ice-cream' },
  { title: 'Iron', icon: 'icon-park:iron' },
  { title: 'Island', icon: 'twemoji:desert-island' },
  { title: 'Jar', icon: 'noto:jar' },
  { title: 'Jellyfish', icon: 'noto:jellyfish' },
  { title: 'Jigsaw', icon: 'twemoji:jigsaw' },
  { title: 'Juice', icon: 'icon-park:juice' },
  { title: 'Key', icon: 'noto:key' },
  { title: 'Kite', icon: 'twemoji:kite' },
  { title: 'Kitten', icon:  'twemoji:cat' },
  { title: 'Koala', icon: 'twemoji:koala' },
  { title: 'Lamp', icon: 'icon-park:desk-lamp' },
  { title: 'Leaf', icon: 'twemoji:maple-leaf' },
  { title: 'Lion', icon: 'twemoji:lion' },
  { title: 'Lollipop', icon: 'fluent-emoji-flat:lollipop' },
  { title: 'Milk', icon: 'twemoji:glass-of-milk'},
  { title: 'Monkey', icon: 'twemoji:monkey'},
  { title: 'Moon', icon: 'fluent-emoji-flat:full-moon-face'},
  { title: 'Mouse', icon: 'twemoji:mouse'},
  { title: 'Nose', icon: 'noto:nose' },
  { title: 'Nest', icon: 'twemoji:empty-nest' },
  {title: 'Numbers', icon: 'noto-v1:input-numbers'},
  { title: 'Nut', icon: 'twemoji:peanuts' },
  { title: 'Octopus', icon: 'twemoji:octopus' },
  { title: 'Onion', icon: 'noto:onion' },
  { title: 'Orange', icon: 'twemoji:orange-heart' },
  { title: 'Owl', icon: 'twemoji:owl' },
  { title: 'Oven', icon: 'icon-park:oven' },  
{ title: 'Piano', icon: 'icon-park:piano' },
{ title: 'Pizza', icon: 'twemoji:pizza' },
{ title: 'Plane', icon: 'twemoji:airplane' },
{ title: 'Pink', icon: 'noto:pink-heart' },
{ title: 'Purple', icon: 'twemoji:purple-heart' },
{ title: 'Pumpkin', icon: 'twemoji:jack-o-lantern' },
{ title: 'Quiet', icon: 'twemoji:shushing-face' },
{ title: 'Red', icon: 'twemoji:red-heart' },
{ title: 'Rocket', icon: 'twemoji:rocket' },
{ title: 'Robot', icon: 'twemoji:robot' },
{ title: 'Rabbit', icon: 'twemoji:rabbit' },
{ title: 'Rainbow', icon: 'twemoji:rainbow' },
{ title: 'Run', icon: 'fluent-emoji-flat:man-running' },
{ title: 'Snail', icon: 'twemoji:snail' },
{ title: 'Star', icon: 'twemoji:star' },
{ title: 'Shoe', icon: 'twemoji:running-shoe' },
{title: 'Slide', icon: 'noto:playground-slide'},
{ title: 'Spider', icon: 'twemoji:spider' },
{ title: 'Sun', icon: 'twemoji:sun' },
{ title: 'Tiger', icon: 'twemoji:tiger' },
{ title: 'Tree', icon: 'emojione:deciduous-tree' },
{ title: 'Truck', icon: 'twemoji:articulated-lorry' },
{ title: 'Train', icon: 'twemoji:station' },
{ title: 'Turtle', icon: 'twemoji:turtle' },
{ title: 'Umbrella', icon: 'twemoji:umbrella' },
{ title: 'Unicorn', icon: 'twemoji:unicorn' },
{ title: 'Volcano', icon: 'twemoji:volcano' },
{ title: 'Van', icon: 'twemoji:minibus' },
{ title: 'Violin', icon: 'twemoji:violin' },
{ title: 'Washer',icon: 'icon-park:washing-machine-one' },
{ title: 'Whale', icon: 'twemoji:whale' },
{ title: 'Water', icon: 'twemoji:droplet' },
{ title: 'Worm', icon: 'twemoji:worm' },
{ title: 'X-ray', icon: 'noto:x-ray' },
{ title: 'Yarn', icon: 'twemoji:yarn' },
{ title: 'Yawn', icon: 'twemoji:yawning-face' },
{ title: 'Yellow', icon: 'twemoji:yellow-heart'},
{ title: 'Yo-yo', icon: 'twemoji:yo-yo' },
{ title: 'Zebra', icon: 'twemoji:zebra' },
{ title: 'Zipper', icon: 'twemoji:zipper-mouth-face' },

]

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
.col-md-6{
text-align: center;
}
</style>