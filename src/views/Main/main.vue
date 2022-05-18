<template>
  <div class="box">
    main
    <button @click="go(3, 3)">初级</button>
    <button @click="go(4, 4)">中级</button>
    <button @click="go(5, 5)">高级</button>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
const router = useRouter();

const go = (vSize: number, hSize: number) => {
  router.push({
    name: "game",
    params: {
      vSize,
      hSize,
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
