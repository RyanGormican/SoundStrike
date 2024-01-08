<template>
  <div id="app">
    <div class="carousel-container">
      <div class="carousel-arrow left" @click="moveCarousel('left')">&#8249;</div>
      <div class="carousel" :style="{ transform: `translateX(${-currentIndex * 50}%)` }">
        <div v-for="(item, index) in visibleItems" :key="index" class="carousel-item">
          <h3>{{ item.title }}</h3>
          <p>{{ item.description }}</p>
        </div>
      </div>
      <div class="carousel-arrow right" @click="moveCarousel('right')">&#8250;</div>
    </div>
  </div>
</template>

<script>
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
      currentIndex: 0,
      itemsPerPage: 4,
    };
  },
  computed: {
    visibleItems() {
      const start = this.currentIndex;
      const end = start + this.itemsPerPage;
      return this.items.slice(start, end);
    },
  },
methods: {
  moveCarousel(direction) {
    const totalItems = this.items.length;

    if (direction === 'left') {
      this.currentIndex = (this.currentIndex - 1 + totalItems) % totalItems;
    } else if (direction === 'right') {
      this.currentIndex = (this.currentIndex + 1) % totalItems;
    }
  },
},
};
</script>

<style>
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden; 
}

.carousel-container {
  display: flex;
  position: relative;
  height: 100vh;
  width: 100vw;
}

.carousel {
  display: flex;
  width: 200%; 
  transition: transform 0.5s ease; 
}

.carousel-item {
  flex: 0 0 50%; 
  box-sizing: border-box;
  padding: 10px;
  text-align: center;
  border: 1px solid #ddd;
}

.carousel-arrow {
  cursor: pointer;
  font-size: 24px;
  margin: 0 10px;
  position: absolute;
  top: 50%;
  color: #333;
}

.left {
  left: 0;
}

.right {
  right: 0;
}
</style>
