<template>
  <div class="robot" :style="{ top: y_position + '%', left: x_position + '%' }">
    <div class="face" :class="direction"></div>
  </div>
</template>

<script>
export default {
  name: "Robot",
  data() {
    return {
      max_x: 80,
      max_y: 80,
      y_position: 0,
      x_position: 0,
      movement_speed: 20,
      direction: "left",
    };
  },
  props: {
    msg: String,
  },
  created() {
    window.addEventListener("keypress", this.doCommand);
  },
  unmounted() {
    window.removeEventListener("keypress", this.doCommand);
  },
  methods: {
    doCommand(e) {
      let cmd = String.fromCharCode(e.keyCode).toLowerCase();

      // for testing the positioning system.
      if (cmd == "s") {
        if (this.y_position < this.max_y) {
          this.y_position += this.movement_speed;
          this.direction = "down";
        }
      }

      if (cmd == "w") {
        if (this.y_position > 0) {
          this.y_position -= this.movement_speed;
          this.direction = "up";
        }
      }

      if (cmd == "d") {
        if (this.x_position < this.max_x) {
          this.x_position += this.movement_speed;
          this.direction = "right";
        }
      }

      if (cmd == "a") {
        if (this.x_position > 0) {
          this.x_position -= this.movement_speed;
          this.direction = "left";
        }
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.robot {
  position: absolute;
  width: 20%;
  height: 20%;
  top: 20%;
  right: 0;

  background: red;
}
.face {
  background: black;
  width: 10%;
  height: 10%;
  position: absolute;
}

.face.left {
  left: 0;
  top: 50%;
  transform: translate(0, -50%);
}

.face.right {
  right: 0;
  top: 50%;
  transform: translate(0, -50%);
}

.face.down {
  left: 50%;
  bottom: 0;
  transform: translate(-50%, 0);
}

.face.up {
  left: 50%;
  top: 0;
  transform: translate(-50%, 0);
}
</style>
