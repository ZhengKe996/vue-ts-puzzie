<template>
  <div
    class="single-puzzle"
    :class="[
      canMove && 'single-puzzle--moveable',
      isBlank && 'single-puzzle--blank',
    ]"
  >
    <div class="single-puzzle__cover" />
  </div>
</template>

<script lang="ts" setup>
import { ref, nextTick } from "vue";

const props = defineProps<{
  canMove?: boolean;
  isBlank?: boolean;
  bgPosition?: string;
  Images: string;
}>();

const bgImg = ref<string | null>(null);
(() => {
  const imgLoader = new Image();
  imgLoader.src = props.Images;
  imgLoader.onload = async () => {
    await nextTick();
    bgImg.value = `url(${props.Images})`;
  };
})();
</script>

<style lang="scss" scoped>
.single-puzzle {
  border-radius: inherit;
  position: relative;

  .single-puzzle__cover {
    @include base__cover;
    @include base__gradient-bg;

    pointer-events: none;

    transition: opacity $base__transition__duration;
    opacity: 0;
  }

  &.single-puzzle--moveable {
    cursor: pointer;

    &:hover .single-puzzle__cover {
      opacity: 0.1;
    }
  }

  &.single-puzzle--blank {
    pointer-events: none;
    opacity: 0;
  }

  &:not(.single-puzzle--blank) {
    background-image: v-bind("bgImg");
    background-size: $base__puzzle-img__width auto;
    background-position: v-bind("props.bgPosition");
    box-shadow: 0 0 3px $base__color--shadow;
  }
}
</style>
