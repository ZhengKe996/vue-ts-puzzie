<template>
  <div class="box">
    main
    <button @click="go">click</button>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
const router = useRouter();

const go = () => {
  router.push("/game");
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
