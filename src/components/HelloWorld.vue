<template>
  <div class="page">
    <div class="container">
      <Moveable
        ref="moveable"
        class="moveable"
        v-bind="moveable"
        @drag="handleDrag"
        @resize="handleResize"
        @scale="handleScale"
        @rotate="handleRotate"
        @warp="handleWarp"
      >
        <span> <img class="moveable" src="@/assets/1.png"></span>
      </Moveable>
      <!-- <Moveable
        ref="moveable"
        class="moveable"
        v-bind="moveable"
        @drag="handleDrag"
        @resize="handleResize"
        @scale="handleScale"
        @rotate="handleRotate"
      >
        <span>
        <img src="@/assets/1.png" />
        </span>
      </Moveable> -->
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
      moveable: {
        draggable: true,
        throttleDrag: 0,
        resizable: false,
        throttleResize: 1,
        keepRatio: true,
        scalable: true,
        throttleScale: 0,
        rotatable: true,
        throttleRotate: 0,
        pinchable: false, // ["draggable", "resizable", "scalable", "rotatable"]
        origin: false,
      },
    };
  },
  mounted() {
    console.log("getRect: ", this.$refs.moveable.getRect());
  },
  methods: {
    change(newRect) {
      this.w = newRect.w;
      this.h = newRect.h;
      this.x = newRect.x;
      this.y = newRect.y;
    },
    handleDrag({ target, transform }) {
      console.log("onDrag left, top", transform);
      target.style.transform = transform;
    },
    handleResize({ target, width, height, delta }) {
      console.log("onResize", width, height);
      delta[0] && (target.style.width = `${width}px`);
      delta[1] && (target.style.height = `${height}px`);
    },
    handleScale({ target, transform, scale }) {
      // eslint-disable-next-line no-debugger
      debugger;
      console.log("onScale scale", scale);
      target.style.transform = transform;
    },
    handleRotate({ target, dist, transform }) {
      console.log("onRotate", dist);
      target.style.transform = transform;
    },
    handleWarp({ target, transform }) {
      console.log("onWarp", transform);
      target.style.transform = transform;
    },
    handlePinch({ target }) {
      console.log("onPinch", target);
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