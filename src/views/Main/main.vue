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
        <span @click="go(3, 3, 0)" class="button lightbg-blue clearfix">
          <span>简单</span>
          <div class="icon">
            <div class="arrow"></div>
          </div>
        </span>

        <span @click="go(4, 4, 1)" class="button lightbg-orange clearfix"
          ><span>中等</span>
          <div class="icon">
            <div class="arrow"></div>
          </div>
        </span>

        <span @click="go(5, 5, 2)" class="button lightbg-pink clearfix"
          ><span>困难</span>
          <div class="icon">
            <div class="arrow"></div>
          </div>
        </span>
      </el-col>
    </el-row>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
import { ElRow, ElCol } from "element-plus";
import { logo } from "@/config";

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

<style scoped lang="less">
.box {
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/images/game-over-bg.jpg");
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

  .button {
    margin: 0 auto;
    width: 11em;
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
    -webkit-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 2px #74b6b4 inset,
      0 4px 0 0 #4a7c7b, 0 5px 0 0 #355655, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 2px #74b6b4 inset,
      0 4px 0 0 #4a7c7b, 0 5px 0 0 #355655, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 2px #74b6b4 inset,
      0 4px 0 0 #4a7c7b, 0 5px 0 0 #355655, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #4e8381 inset, 0 0 0 2px #74b6b4 inset,
      0 4px 0 0 #4a7c7b, 0 5px 0 0 #355655, 0 8px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-blue:hover {
    background-color: #73c2c0;
  }
  .lightbg-blue:active {
    background-color: #5a9896;
    -webkit-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 2px #65a9a7 inset,
      0 0.0625em 0 0 #355655, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 2px #65a9a7 inset,
      0 0.0625em 0 0 #355655, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 2px #65a9a7 inset,
      0 0.0625em 0 0 #355655, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #589391 inset, 0 0 0 2px #65a9a7 inset,
      0 0.0625em 0 0 #355655, 0 3px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-blue .arrow {
    border-color: transparent transparent transparent #74b6b4;
  }
  .icon {
    width: 1.625em;
    height: 1.625em;
    -webkit-border-radius: 13px;
    -moz-border-radius: 13px;
    -ie-border-radius: 13px;
    border-radius: 13px;
    background: rgba(0, 0, 0, 0.3);
    float: right;
    -webkit-box-shadow: 0 3px 0 0 rgba(0, 0, 0, 0.2) inset,
      0 0 0 0.0625em rgba(255, 255, 255, 0.2);
    -moz-box-shadow: 0 3px 0 0 rgba(0, 0, 0, 0.2) inset,
      0 0 0 0.0625em rgba(255, 255, 255, 0.2);
    -ie-box-shadow: 0 3px 0 0 rgba(0, 0, 0, 0.2) inset,
      0 0 0 0.0625em rgba(255, 255, 255, 0.2);
    box-shadow: 0 3px 0 0 rgba(0, 0, 0, 0.2) inset,
      0 0 0 0.0625em rgba(255, 255, 255, 0.2);
  }
  .arrow {
    margin: 7px 0 0 8px;
    -webkit-border-style: solid;
    -moz-border-style: solid;
    -ie-border-style: solid;
    border-style: solid;
    border-width: 0.375em 0.375em 0.375em 0.75em;
    width: 0;
    height: 0;
  }

  .lightbg-orange {
    background-color: #e65440;
    color: #ffdada;
    -webkit-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 4px 0 0 #a53c2e, 0 5px 0 0 #7e2e23, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 4px 0 0 #a53c2e, 0 5px 0 0 #7e2e23, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 4px 0 0 #a53c2e, 0 5px 0 0 #7e2e23, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 4px 0 0 #a53c2e, 0 5px 0 0 #7e2e23, 0 8px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-orange:hover {
    background-color: #f15843;
  }
  .lightbg-orange:active {
    background-color: #d54e3b;
    -webkit-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 0.0625em 0 0 #a53c2e, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 0.0625em 0 0 #a53c2e, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 0.0625em 0 0 #a53c2e, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #b24132 inset, 0 0 0 2px #ea624a inset,
      0 0.0625em 0 0 #a53c2e, 0 3px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-orange .arrow {
    border-color: transparent transparent transparent #ea624a;
  }

  .lightbg-pink {
    background-color: #cc3747;
    color: #ffdada;
    -webkit-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 4px 0 0 #8d1b27, 0 5px 0 0 #65141c, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 4px 0 0 #8d1b27, 0 5px 0 0 #65141c, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 4px 0 0 #8d1b27, 0 5px 0 0 #65141c, 0 8px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 4px 0 0 #8d1b27, 0 5px 0 0 #65141c, 0 8px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-pink:hover {
    background-color: #dd3c4d;
  }
  .lightbg-pink:active {
    background-color: #bb3241;
    -webkit-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 0.0625em 0 0 #8d1b27, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 0.0625em 0 0 #8d1b27, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    -ie-box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 0.0625em 0 0 #8d1b27, 0 3px 0 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 0 0.0625em #8d1b27 inset, 0 0 0 2px #dd4356 inset,
      0 0.0625em 0 0 #8d1b27, 0 3px 0 0 rgba(0, 0, 0, 0.15);
  }
  .lightbg-pink .arrow {
    border-color: transparent transparent transparent #dd4356;
  }
}
</style>
