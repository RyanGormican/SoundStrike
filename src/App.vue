<template>
  <div id="app">
    <div class="container">
      <div id="myCarousel" class="carousel slide" data-ride="carousel">
        <div class="carousel-inner">
          <div v-for="(item, index) in items" :key="index" :class="{ 'carousel-item': true, active: index === 0 }">
            <div class="row">
              <div v-for="(letter, letterIndex) in ['a', 'b', 'c', 'd']" :key="letterIndex" class="col-md-6">
                <h3>{{ items[(index * 4 + letterIndex) % items.length].title }}</h3>
                <p>{{ items[(index * 4 + letterIndex) % items.length].description }}</p>
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

export default {
  name: 'App',
  data() {
    return {
      items: [
        { title: 'Item 1', description: 'Description 1' },
        { title: 'Item 2', description: 'Description 2' },
        { title: 'Item 3', description: 'Description 3' },
        { title: 'Item 4', description: 'Description 4' },
        { title: 'Item 5', description: 'Description 5' },
        { title: 'Item 6', description: 'Description 6' },
        { title: 'Item 7', description: 'Description 7' },
        { title: 'Item 8', description: 'Description 8' },
      ],
    };
  },
};
</script>

<style>
#app {
  overflow: hidden;
  background-color: lightblue;
  min-height:100vh;
}


</style>
