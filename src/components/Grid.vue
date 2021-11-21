<template>
  <div class="grid">
    <Robot />
  </div>
  <label>Input</label>
  <input type="text" class="main-input" />
  <button>Go!</button>
</template>

<script>
import Robot from "./Robot.vue";
export default {
  name: "Grid",
  props: {
    msg: String,
  },
  data() {
    return {
      movement_input: "",
    };
  },
  components: {
    Robot,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grid {
  position: relative;
  width: 50%;
  background: blue;
  margin: auto;
}
.grid:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}
label {
  text-align: center;
  display: block;
  margin: 50px auto 10px auto;
}
.main-input {
  margin: 0 auto;
  display: block;
}
button {
  display: block;
  margin: 10px auto 0 auto;
}
</style>
