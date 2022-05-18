<template>
  <div id="background">
    <div
      class="background__img-cover"
      :class="!bgImg && 'background__img-cover--hidden'"
    />
  </div>
</template>

<script setup lang="ts">
import { ref, nextTick } from "vue";
import { gameBg } from "@/config";

const bgImg = ref<string | null>(null);
(() => {
  const imgLoader = new Image();
  imgLoader.src = gameBg;
  imgLoader.onload = async () => {
    await nextTick();
    bgImg.value = `url(${gameBg})`;
  };
})();
</script>

<style lang="scss">
#background {
  @include base__cover;

  z-index: -1;
  pointer-events: none;
  background: $base__color--primary;

  .background__img-cover {
    @include base__cover;

    background: v-bind("bgImg") center / cover no-repeat fixed;
    filter: grayscale(100%);

    transition: opacity $base__transition__duration;
    opacity: 1;

    &.background__img-cover--hidden {
      opacity: 0;
    }
  }
}
</style>
