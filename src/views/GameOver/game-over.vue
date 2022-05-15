<template>
  <div>
    game-over----{{ route.params.time }}-------{{ route.params.moveCount }}
  </div>
</template>

<script setup lang="ts">
import { useRoute } from "vue-router";
const route = useRoute();
</script>

<style scoped></style>
