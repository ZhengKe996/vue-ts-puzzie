<template>
  <div class="box">
    <div class="popup">
      <div class="title">游戏结束</div>
      <div class="content">用时: {{ route.params.time }}秒</div>
      <div class="content">移动步数: {{ route.params.moveCount }}次</div>
      <div class="details">
        <p></p>
      </div>
      <div class="btn-box">
        <KBlueButton :text="'再试一次'"></KBlueButton>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRoute } from "vue-router";
import { KBlueButton } from "@/component/KButton";
const route = useRoute();
</script>

<style scoped lang="scss">
.box {
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/images/game-over-bg.jpg");
  background-repeat: no-repeat;
  background-size: 100vw 100vh;
  overflow: hidden;

  .popup {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 85vw;
    height: 75vh;
    background-color: rgba(255, 255, 255, 0.5);
    border-radius: 1em;
    margin: 2em;
    text-align: center;
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    .btn-box {
      padding: 16rem auto 0;
    }
    .title {
      font-size: 2rem;
      margin: 0.5rem;
    }
    .content {
      font-size: 1.5rem;

      margin: 1rem;
    }
    .details {
      height: 35vh;
      overflow: hidden;
      overflow-y: scroll;
      font-size: 0.8rem;
      text-indent: 2em;
      text-align: left;
      color: #666;
      line-height: 1.5em;
      font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
        "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
      margin: 1rem;
    }
  }
}
</style>
