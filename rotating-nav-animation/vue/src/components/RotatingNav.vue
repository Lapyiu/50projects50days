<template>
  <div class="rotating-nav">
    <div :class="{ container: true, 'show-nav': showNav }">
      <div class="circle-container">
        <div class="circle">
          <button id="close" @click="closeClick">
            <i class="fas fa-times"></i>
          </button>
          <button id="open" @click="openClick">
            <i class="fas fa-bars"></i>
          </button>
        </div>
      </div>
      <div class="content">
          <slot name="content">這是slot</slot>
      </div>
    </div>

    <nav>
      <ul>
        <li v-for="(item,index) of menus" :key="index">
          <i :class="'fas fa-' + item"></i><a href="#"> {{ item }}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: "RotatingNav",
  props: {
    menus: {
      type: Array,
      default() {
        return ["HOME", "ABOUT", "CONTACT"];
      },
    },
    showNav: {
      type: Boolean,
      default() {
        return false;
      },
    },
  },
  methods: {
    closeClick() {
      this.showNav = false;
    },
    openClick() {
      this.showNav = true;
    },
  },
};
</script>

<style scoped>

.container {
  background-color: #fafafa;
  transform-origin: top left;
  transition: transform 0.5s linear;
  width: 100vw;
  min-height: 100vh;
  padding: 50px;
}

.container.show-nav {
  transform: rotate(-20deg);
}

.circle-container {
  position: fixed;
  top: -100px;
  left: -100px;
}

.circle {
  background-color: #ff7979;
  height: 200px;
  width: 200px;
  border-radius: 50%;
  position: relative;
  transition: transform 0.5s linear;
}

.container.show-nav .circle {
  transform: rotate(-70deg);
}

.circle button {
  cursor: pointer;
  position: absolute;
  top: 50%;
  left: 50%;
  height: 100px;
  background: transparent;
  border: 0;
  font-size: 26px;
  color: #fff;
}

.circle button:focus {
  outline: none;
}

.circle button#open {
  left: 60%;
}

.circle button#close {
  top: 60%;
  transform: rotate(90deg);
  transform-origin: top left;
}

.container.show-nav + nav li {
  transform: translateX(0);
  transition-delay: 0.3s;
}

nav {
  position: fixed;
  bottom: 40px;
  left: 0;
  z-index: 100;
}

nav ul {
  list-style-type: none;
  padding-left: 30px;
}

nav ul li {
  text-transform: uppercase;
  color: #fff;
  margin: 40px 0;
  transform: translateX(-100%);
  transition: transform 0.4s ease-in;
}

nav ul li i {
  font-size: 20px;
  margin-right: 10px;
}

nav ul li + li {
  margin-left: 15px;
  transform: translateX(-150%);
}

nav ul li + li + li {
  margin-left: 30px;
  transform: translateX(-200%);
}

nav a {
  color: #fafafa;
  text-decoration: none;
  transition: all 0.5s;
}

nav a:hover {
  color: #ff7979;
  font-weight: bold;
}

.content img {
  max-width: 100%;
}

.content {
  max-width: 1000px;
  margin: 50px auto;
}

.content h1 {
  margin: 0;
}

.content small {
  color: #555;
  font-style: italic;
}

.content p {
  color: #333;
  line-height: 1.5;
}
</style>
