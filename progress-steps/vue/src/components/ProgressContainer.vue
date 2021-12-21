<template>
  <div class="container">
    <div class="progress-container">
      <div class="progress" id="progress" :style="{ width: progressWidth }" />
      <div
        :class="{ circle: true, active: isActived(index) }"
        v-for="(item, index) of size"
        :key="index"
      >
        {{ index + 1 }}
      </div>
    </div>


    <button
      class="btn"
      id="prev"
      :disabled="currentActive === 1"
      @click="clickPrev"
    >
      Prev
    </button>
    <button
      class="btn"
      id="next"
      :disabled="currentActive === size"
      @click="clickNext"
    >
      Next
    </button>
  </div>
</template>

<script>
export default {
  name: "ProgressContainer",
  props: {
    size: {
      type: Number,
      default: function () {
        return 4;
      },
    },
  },
  data() {
    return {
      currentActive: 1,
    };
  },
  methods: {
    clickNext() {
      console.log("++++++++++++++++");
      this.currentActive++;
      if (this.currentActive > this.size) {
        this.currentActive = this.size;
      }
      console.log(this.currentActive);
    },
    clickPrev() {
      console.log("-------------------");
      this.currentActive--;
      if (this.currentActive < 1) {
        this.currentActive = 1;
      }
      console.log(this.currentActive);
    },
    isActived(index) {
      return this.currentActive >= index + 1;
    },
  },
  computed: {
    progressWidth() {
      return (
        ((this.currentActive - 1) / (this.size - 1)) * 100 + "%"
      );
    },
  },
};
</script>

<style scoped>
.container {
  text-align: center;
}

.progress-container {
  display: flex;
  justify-content: space-between;
  position: relative;
  margin-bottom: 30px;
  max-width: 100%;
  width: 350px;
}

.progress-container::before {
  content: "";
  background-color: var(--line-border-empty);
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  height: 4px;
  width: 100%;
  z-index: -1;
}

.progress {
  background-color: var(--line-border-fill);
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  height: 4px;
  width: 0%;
  z-index: -1;
  transition: 0.4s ease;
}

.circle {
  background-color: #fff;
  color: #999;
  border-radius: 50%;
  height: 30px;
  width: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 3px solid var(--line-border-empty);
  transition: 0.4s ease;
}

.circle.active {
  border-color: var(--line-border-fill);
}

.btn {
  background-color: var(--line-border-fill);
  color: #fff;
  border: 0;
  border-radius: 6px;
  cursor: pointer;
  font-family: inherit;
  padding: 8px 30px;
  margin: 5px;
  font-size: 14px;
}

.btn:active {
  transform: scale(0.98);
}

.btn:focus {
  outline: 0;
}

.btn:disabled {
  background-color: var(--line-border-empty);
  cursor: not-allowed;
}
</style>
