<template>
  <div class="container">
    <img
      src="@/assets/2.png"
      alt=""
    >
    <Movable />
  </div>
</template>

<script>
// @ is an alias to /src
import Movable from "@/components/Movable.vue";

export default {
  name: "Home",
  components: {
    Movable,
  },
};
</script>
<style scoped>
.container {
  width: 100%;
  position: relative;
}
</style>
