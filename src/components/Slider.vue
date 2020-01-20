<template>
  <header class="header">
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <img :src="currentImg" />
        <div class="slide-content">
          <div class="slide-content-heading">
            <h1 class="slide-heading">One Page</h1>
            <h2 class="slide-subheading">multi-purpose Theme</h2>
          </div>
          <p class="slide-paragraph">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Possimus vel mollitia dolor iusto laboriosam totam consectetur voluptatem est quam doloribus.</p>
          <button class="btn-started">get started</button>
        </div>
      </div>
    </transition-group>
    <div class="menu">
      <h4 class="menu-heading">MENU</h4>
      <div class="menu-icon">
        <div class="line line-1"></div>
        <div class="line line-2"></div>
        <div class="line line-3"></div>
      </div>
    </div>
    <a class="prev" @click="prev" href="#">&#10094;</a>
    <a class="next" @click="next" href="#">&#10095;</a>
  </header>
</template>
<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
        "https://cdn.pixabay.com/photo/2015/12/12/15/24/amsterdam-1089646_1280.jpg",
        "https://cdn.pixabay.com/photo/2016/02/17/23/03/usa-1206240_1280.jpg",
        "https://cdn.pixabay.com/photo/2015/05/15/14/27/eiffel-tower-768501_1280.jpg",
        "https://cdn.pixabay.com/photo/2016/12/04/19/30/berlin-cathedral-1882397_1280.jpg"
      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 10000);
    },

    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
};
</script>

<style scoped>
.header {
  position: relative;
}
.menu {
  position: absolute;
  display: flex;
  z-index: 10;
  cursor: pointer;
  top: 3.5rem;
  right: 5rem;
}

.menu-heading {
  font-size: 1rem;
  color: #ffffff;
  margin: 0;
  font-family: "Raleway", sans-serif;
}

.line {
  height: 0.2rem;
  width: 1.5rem;
  background-color: #fff;
  margin-bottom: 0.2rem;
  margin-left: 0.3rem;
}

.slide-content {
  z-index: 10;
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  top: -2rem;
}

.slide-heading {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  font-size: 4rem;
  text-transform: uppercase;
  color: #ffffff;
  font-weight: 600;
  letter-spacing: 0.3rem;
}

.slide-subheading {
  font-family: 'Open Sans', sans-serif;
  font-size: 1.9rem;
  text-transform: uppercase;
  color: #ffffff;
  font-weight: 300;
  margin: 0;
  letter-spacing: 0.2rem;
}

.slide-content-heading {
  border-top: 0.4rem solid #ffffff;
  border-bottom: 0.4rem solid #ffffff;
}


.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width: 100%;
  opacity: 1;
}

.slide-paragraph {
  margin: 4rem 0;
  font-size: 0.9rem;
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
}

.btn-started {
  background: transparent;
  color: #ffffff;
  border: 0.1rem solid #fff;
  text-transform: uppercase;
  padding: 0.5rem;
  width: 10rem;
  outline: none;
  transition: all 0.5s;
}
.btn-started:hover {
  color: #5cc9c1;
  border: 0.1rem solid #5cc9c1;
  cursor: pointer;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width: 100%;
  opacity: 0;
}

img {
  height: 600px;
  width: 100%;
}

.prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.9);
}
</style>
