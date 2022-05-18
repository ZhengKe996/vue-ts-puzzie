<template>
  <div class="box">
    main
    <button @click="go(3, 3, 0)">初级</button>
    <button @click="go(4, 4, 1)">中级</button>
    <button @click="go(5, 5, 2)">高级</button>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
const router = useRouter();

const go = (vSize: number, hSize: number, checkpoint: number) => {
  router.push({
    name: "game",
    params: {
      vSize,
      hSize,
      checkpoint,
    },
  });
};
</script>

<style scoped>
.box {
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/images/bg.png");
  background-repeat: no-repeat;
  background-size: 100vw 100vh;
}
</style>
