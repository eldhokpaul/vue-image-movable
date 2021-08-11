<template>
  <div class="page">
    <div class="container">
      <vue-drr
        :x="x"
        :y="y"
        :angle="angle"
        :w="width"
        :h="height"
        :parent="true"
        @dragging="handleDragging"
        @resizing="handleResizing"
        @rotating="handleRotating"
      >
        <span>
          <img class="moveable" src="@/assets/1.png" />
        </span>
      </vue-drr>
    </div>
  </div>
</template>

<script>
import VueDrr from "vue-drr";
export default {
  name: "Home",
  components: {
    VueDrr,
  },
  data() {
    return {
      width: 200,
      height: 200,
      x: 50,
      y: 50,
      angle: 0,
    };
  },
  mounted() {},
  methods: {
    handleResizing: function (x, y, width, height) {
      this.x = x;
      this.y = y;
      this.width = width;
      this.height = height;
    },
    handleDragging: function (x, y) {
      this.x = x;
      this.y = y;
    },
    handleRotating: function (angle) {
      this.angle = angle;
    },
  },
};
</script>
<style scoped>
.wrapper {
  width: 100%;
}
.cell {
  width: 50%;
  float: leftF;
}
.container {
  position: absolute;
  top: 30px;
  left: 60px;
  width: 500px;
  height: 500px;
  margin: 20px;
  border: 1px solid red;
}

.moveable {
  position: relative;
  width: 250px;
  height: 250px;
  margin: 0 auto;
}
.page {
  position: relative;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
}
</style>