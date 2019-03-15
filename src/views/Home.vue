<template>
  <div id="container">
    <Back2Top4Vue id="back" color="#eeeeee" backgroundColor="green"></Back2Top4Vue>
  </div>
</template>

<script>
import Back2Top4Vue from "back2top4vue";
export default {
  components: {
    Back2Top4Vue
  }
};
</script>

<style scoped>
#container {
  height: calc(100vh + 800px);
  width: calc(100vw + 200px);
}
#back {
  position: fixed;
  right: 20px;
  bottom: 100px;
  overflow: 999;
}
</style>
