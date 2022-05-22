<template>
  <span class="button lightbg-blue clearfix">
    <span>{{ props.text }}</span>
    <div class="icon">
      <div class="arrow"></div>
    </div>
  </span>
</template>

<script setup lang="ts">
import { defineProps } from "vue";

const props = defineProps<{ text: string }>();
</script>

<style scoped>
.button {
  margin: 0 auto;
  width: 11rem;
  height: 1.75em;
  display: block;
  -webkit-border-radius: 0.375em;
  -moz-border-radius: 0.375em;
  -ie-border-radius: 0.375em;
  border-radius: 0.375em;
  padding: 0.48em 0.8em;
  text-shadow: rgba(0, 0, 0, 0.5) 0 -0.0625em 0;
  font-size: 1.125em;
  font-weight: 700;
  -webkit-transition-property: background-color;
  -webkit-transition-duration: 0.15s;
  -webkit-transition-timing-function: ease-in-out;
  cursor: pointer;
  text-decoration: none;
  margin-bottom: 1.25em;
}
.button:active {
  margin-top: 1.5625em;
  margin-bottom: 0.9375em;
}
.button span {
  vertical-align: middle;
  font-size: 1.2em;
}
.lightbg-blue {
  background-color: #64a8a6;
  color: #dafffe;
  -webkit-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 0.125em #74b6b4 inset,
    0 0.25em 0 0 #4a7c7b, 0 0.3125em 0 0 #355655,
    0 0.5em 0 0 rgba(0, 0, 0, 0.15);
  -moz-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 0.125em #74b6b4 inset,
    0 0.25em 0 0 #4a7c7b, 0 0.3125em 0 0 #355655,
    0 0.5em 0 0 rgba(0, 0, 0, 0.15);
  -ie-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 0.125em #74b6b4 inset,
    0 0.25em 0 0 #4a7c7b, 0 0.3125em 0 0 #355655,
    0 0.5em 0 0 rgba(0, 0, 0, 0.15);
  box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 0.125em #74b6b4 inset,
    0 0.25em 0 0 #4a7c7b, 0 0.3125em 0 0 #355655,
    0 0.5em 0 0 rgba(0, 0, 0, 0.15);
}
.lightbg-blue:hover {
  background-color: #73c2c0;
}
.lightbg-blue:active {
  background-color: #5a9896;
  -webkit-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 0.125em #65a9a7 inset,
    0 0.0625em 0 0 #355655, 0 0.1875em 0 0 rgba(0, 0, 0, 0.15);
  -moz-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 0.125em #65a9a7 inset,
    0 0.0625em 0 0 #355655, 0 0.1875em 0 0 rgba(0, 0, 0, 0.15);
  -ie-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 0.125em #65a9a7 inset,
    0 0.0625em 0 0 #355655, 0 0.1875em 0 0 rgba(0, 0, 0, 0.15);
  box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 0.125em #65a9a7 inset,
    0 0.0625em 0 0 #355655, 0 0.1875em 0 0 rgba(0, 0, 0, 0.15);
}
.lightbg-blue .arrow {
  border-color: transparent transparent transparent #74b6b4;
}
.icon {
  width: 1.625em;
  height: 1.625em;
  -webkit-border-radius: 0.8125em;
  -moz-border-radius: 0.8125em;
  -ie-border-radius: 0.8125em;
  border-radius: 0.8125em;
  background: rgba(0, 0, 0, 0.3);
  float: right;
  -webkit-box-shadow: 0 0.1875em 0 0 rgba(0, 0, 0, 0.2) inset,
    0 0 0 0.0625em rgba(255, 255, 255, 0.2);
  -moz-box-shadow: 0 0.1875em 0 0 rgba(0, 0, 0, 0.2) inset,
    0 0 0 0.0625em rgba(255, 255, 255, 0.2);
  -ie-box-shadow: 0 0.1875em 0 0 rgba(0, 0, 0, 0.2) inset,
    0 0 0 0.0625em rgba(255, 255, 255, 0.2);
  box-shadow: 0 0.1875em 0 0 rgba(0, 0, 0, 0.2) inset,
    0 0 0 0.0625em rgba(255, 255, 255, 0.2);
}
.arrow {
  margin: 0.4375em 0 0 0.5em;
  -webkit-border-style: solid;
  -moz-border-style: solid;
  -ie-border-style: solid;
  border-style: solid;
  border-width: 0.375em 0.375em 0.375em 0.75em;
  width: 0;
  height: 0;
}
</style>
