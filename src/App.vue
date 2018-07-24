<template>
  <div class="container">
    <p><input type="range" min="0" max="100" v-model.number="amount"></p>
    <MyCanvas :amount="amount"/>
  </div>
</template>

<script>
import MyCanvas from "./components/MyCanvas";
export default {
  components: {
    MyCanvas
  },
  data() {
    return {
      amount: 50
    };
  }
};
</script>

<style lang="scss">
html {
  height: 100%;
}
body {
  // background: #000;
  margin: 0;
  height: 100%;
}
.container {
  height: 100%;
}
</style>
