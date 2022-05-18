<template>
  <Background />

  <Controls
    :move-count="moveCount"
    :time="time"
    @shuffle-puzzle="shuffleUserPuzzle"
  />

  <Puzzle
    :h-size="hSize"
    :v-size="vSize"
    :are-puzzle-ordered-correctly="arePuzzleOrderedCorrectly"
    :base-puzzle="basePuzzle"
    :user-puzzle="userPuzzle"
    @swap-user-puzzle="swapUserPuzzle"
    :game-page="gamePage"
  />

  <Footer />
</template>

<script setup lang="ts">
import { computed, reactive, ref, watch } from "vue";
import { useRouter, useRoute } from "vue-router";
import { gamePage } from "@/config";
import Footer from "@/component/Footer";
import Background from "@/component/Background";
import Puzzle from "@/component/Puzzle";
import Controls from "@/component/Controls";

const route = useRoute();
const router = useRouter();

const go = () => {
  router.push({
    name: "game-over",
    params: {
      time: time.value,
      moveCount: moveCount.value,
      hSize: route.params.vSize,
      vSize: route.params.vSize,
    },
  });
};
const hSize = ref(Number(route.params.hSize));
const vSize = ref(Number(route.params.vSize));

const basePuzzle = computed(() =>
  Array.from({ length: hSize.value * vSize.value }, (_, i) => i)
);

const userPuzzle = reactive<number[]>([]);

const arePuzzleOrderedCorrectly = computed(() => {
  for (let i = 0; i < basePuzzle.value.length; i++) {
    if (basePuzzle.value[i] !== userPuzzle[i]) {
      return false;
    }
  }

  return true;
});

const moveCount = ref(0);
const time = ref(0);
let timeInterval: number;

const getShuffledPuzzle = () => {
  const newPuzzle = basePuzzle.value.slice(0, -1);

  for (let index = newPuzzle.length - 1; index > 0; index--) {
    const targetIndex = Math.floor(Math.random() * (index + 1));
    [newPuzzle[index], newPuzzle[targetIndex]] = [
      newPuzzle[targetIndex],
      newPuzzle[index],
    ];
  }

  newPuzzle.push(basePuzzle.value[basePuzzle.value.length - 1]);

  return newPuzzle;
};

const shuffleUserPuzzle = () => {
  do {
    userPuzzle.splice(0, userPuzzle.length, ...getShuffledPuzzle());
  } while (arePuzzleOrderedCorrectly.value);

  moveCount.value = 0;
  time.value = 0;
};

const swapUserPuzzle = ({
  indexA,
  indexB,
}: {
  indexA: number;
  indexB: number;
}) => {
  [userPuzzle[indexA], userPuzzle[indexB]] = [
    userPuzzle[indexB],
    userPuzzle[indexA],
  ];

  moveCount.value++;
};

watch(moveCount, (value) => {
  if (value === 0) {
    clearInterval(timeInterval);
    return;
  }

  if (value === 1) {
    clearInterval(timeInterval);
    // @ts-ignore
    timeInterval = setInterval(() => {
      time.value++;
    }, 1000);
  }
});

watch(arePuzzleOrderedCorrectly, (value) => {
  console.log("跳转到游戏结束页面");
  go();
  if (value) {
    clearInterval(timeInterval);
  }
});

watch(basePuzzle, shuffleUserPuzzle);
shuffleUserPuzzle();
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  max-width: 100vw;
  max-height: 100vh;
  padding: 0;
  margin: 0;
  position: relative;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}
</style>
