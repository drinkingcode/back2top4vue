<template>
  <svg
    version="1.1"
    baseProfile="full"
    width="60"
    height="60"
    xmlns="http://www.w3.org/2000/svg"
    @click="onClick"
  >
    <circle cx="30" cy="30" r="30" :fill="circleColor"></circle>
    <path
      d="M20 17 L40 17 M20 30 L30 20 M40 30 L30 20 M30 43 L30 20"
      :stroke="lineColor"
      stroke-width="2"
    ></path>
  </svg>
</template>


<script>
export default {
  props: {
    color: {
      type: String,
      default: "white"
    },
    backgroundColor: {
      type: String,
      default: "green"
    }
  },
  data() {
    return {
      circleColor: this.backgroundColor,
      lineColor: this.color,
      requestId: ""
    };
  },
  methods: {
    onClick() {
      if (window.pageYOffset > 0) {
        this.requestId = window.requestAnimationFrame(this.onClick);
        if (window.pageYOffset < 10) {
          window.scrollTo(window.pageXOffset, 0);
        } else {
          window.scrollTo(
            window.pageXOffset,
            window.pageYOffset - window.pageYOffset / 5
          );
        }
      } else {
        if (this.requestId) {
          window.cancelAnimationFrame(this.requestId);
        }
      }
    }
  },
  beforeDestroy: function() {
    if (this.requestId) {
      window.cancelAnimationFrame(this.requestId);
    }
  }
};
</script>

<style scoped>
svg:hover {
  cursor: pointer;
  opacity: 0.8;
}
</style>

