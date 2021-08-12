<template>
  <div>
    <div class="container">
      <div class="cell">
        <img 
          src="@/assets/2.png" 
          alt=""
        >
      </div>
      <div class="cell">
        <vue-drr
          :x="x"
          :y="y"
          :angle="angle"
          :w="width"
          :h="height"
          @dragging="handleDragging"
          @resizing="handleResizing"
          @rotating="handleRotating"
        >
          <img 
            :style="style" 
            src="@/assets/1.png"
          >
          <!-- <img
            :style="{
              top: x + 'px',
              left: y + 'px',
              width: width + 'px',
              height: height + 'px',
            }"
            src="@/assets/1.png"
          /> -->
        </vue-drr>
      </div>
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
  data: function () {
    return {
      width: 200,
      height: 200,
      x: 1000,
      y: 50,
      angle: 0,
    };
  },
  computed: {
    style() {
      return {
        top: this.x + "px",
        left: this.y + "px",
        width: this.width + "px",
        height: this.height + "px",
        transform: "rotate(" + this.angle + "deg)",
      };
    },
  },
  methods: {
    handleResizing: function (x, y, width, height) {
      this.x = x;
      this.y = y;
      this.width = width;
      this.height = height;
      // this.height = width;
      // console.log(height);
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
<style>
.container {
  widows: 50%;
  position: relative;
}
.cell {
  width: 50%;
  float: leftF;
}
</style>
