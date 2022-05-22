<template>
  <div class="box">
    <el-row>
      <el-col :span="24">
        <img class="logo" :src="logo" alt="" />
      </el-col>
    </el-row>

    <el-row>
      <el-col :span="24">
        <div class="title" data-attr="快来拼一拼">快来拼一拼</div>
      </el-col>
    </el-row>

    <el-row>
      <el-col :span="24" class="buttons">
        <KBlueButton @click="go(3, 3, 0)" :text="'简单'"></KBlueButton>
        <KOrangeutton @click="go(4, 4, 1)" :text="'困难'"></KOrangeutton>
        <KPinkutton @click="go(5, 5, 2)" :text="'地狱'"></KPinkutton>
      </el-col>
    </el-row>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
import { ElRow, ElCol } from "element-plus";
import { logo } from "@/config";
import { KBlueButton, KOrangeutton, KPinkutton } from "@/component/KButton";

const router = useRouter();

const go = (vSize: number, hSize: number, checkpoint: number) => {
  setTimeout(() => {
    router.push({
      name: "game",
      params: {
        vSize,
        hSize,
        checkpoint,
      },
    });
  }, 1000);
};
</script>

<style scoped lang="scss">
.box {
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/images/main-bg.jpg");
  background-repeat: no-repeat;
  background-size: 100vw 100vh;
  overflow: hidden;

  .logo {
    width: 10rem;
    height: 3rem;
    padding: 1rem;
    position: fixed;
    top: 0;
    right: 0;
  }

  .title {
    text-align: center;
    font: bold 3em Consolas, Monaco, monospace;
    border-right: 0.1em solid;
    width: 75vw;
    margin: 2em 1em;
    white-space: nowrap;
    overflow: hidden;
    animation: typing 3s steps(26, end),
      cursor-blink 0.3s step-end infinite alternate;
  }
  @keyframes typing {
    from {
      width: 0;
    }
  }

  @keyframes cursor-blink {
    50% {
      border-color: transparent;
    }
  }
}
</style>
