<template>
  <div class="page">
    <div class="container">
      <Moveable
        ref="moveable"
        :disabled="active"
        class="moveable"
        v-bind="moveable"
        @activated="onActivated"
        @deactivated="onActivated"
        @drag="handleDrag"
        @resize="handleResize"
        @scale="handleScale"
        @rotate="handleRotate"
        @warp="handleWarp"
      >
        <div class="moveable">
          <img class="moveable" src="@/assets/1.png" />
        </div>
      </Moveable>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import VueDragResizeAndRotate from "vue-drag-resize-and-rotate";
import Moveable from "vue-moveable";
export default {
  name: "Home",
  components: {
    // VueDragResizeAndRotate,
    Moveable,
  },
  data() {
    return {
      w: 200,
      h: 200,
      x: 0,
      y: 0,
      active: true,
      moveable: {
        draggable: true,
        throttleDrag: 1,
        throttleResize: 1,
        keepRatio: true,
        scalable: true,
        throttleScale: 0.01,
        rotatable: true,
        throttleRotate: 0.2,
        pinchable: true,
      },
    };
  },
  mounted() {},
  methods: {
    onActivated() {
      this.active = !this.active;
    },
    change(newRect) {
      this.w = newRect.w;
      this.h = newRect.h;
      this.x = newRect.x;
      this.y = newRect.y;
    },
    handleDrag({ target, transform }) {
      target.style.transform = transform;
    },
    handleResize({ target, width, height, delta }) {
      delta[0] && (target.style.width = `${width}px`);
      delta[1] && (target.style.height = `${height}px`);
    },
    handleScale({ target, transform }) {
      target.style.transform = transform;
    },
    handleRotate({ target, transform }) {
      target.style.transform = transform;
    },
    handleWarp({ target, transform }) {
      target.style.transform = transform;
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
  widows: 50%;
  position: relative;
  /* top: 50%; */
  /* left: 50%; */
  /* transform: translate(-90%, -90%); */
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