<template>
  <div
    :class="{ panel: true, active: active }"
    @click="itemClick(index)"
    :style="{ 'background-image': 'url(' + url + ')' }"
  >
    <h3>{{ text }}</h3>
  </div>
</template>

<script>
export default {
  name: "Panel",
  props: {
    index: {
      type: Number,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      default: "",
    },
    active: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    itemClick(index) {
      this.$emit("itemClick", index);
    },
  },
};
</script>

<style scoped>
.panel {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  flex: 0.5;
  margin: 10px;
  position: relative;
  -webkit-transition: all 700ms ease-in;
}

.panel h3 {
  font-size: 24px;
  position: absolute;
  bottom: 20px;
  left: 20px;
  margin: 0;
  opacity: 0;
}

.panel.active {
  flex: 5;
}

.panel.active h3 {
  opacity: 1;
  transition: opacity 0.3s ease-in 0.4s;
}

@media (max-width: 480px) {
  .container {
    width: 100vw;
  }

  .panel:nth-of-type(4),
  .panel:nth-of-type(5) {
    display: none;
  }
}
</style>
