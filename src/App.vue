<template>
  <div class="container">
    <div class="grid">
      <div class="grid-col grid-main">
        <img src="/res/img/lufei.jfif" alt="" />
      </div>
      <div class="grid-col grid-banner">
        <div class="text" data-title="双刃战意">双刃战意</div>
      </div>
      <div class="grid-col grid-icon">
        <img src="/res/svg/vuejs.svg" alt="" />
      </div>
      <div class="grid-col grid-icon" style="--i: 1">
        <img src="/res/svg/vite.svg" alt="" />
      </div>
      <div class="grid-col grid-noBg" style="--i: 2">
        <img src="/res/svg/bzhan.svg" alt="" />
      </div>
      <div class="grid-col grid-noBg" style="--i: 3">
        <img src="/res/img/codepen.webp" alt="" />
      </div>
      <div class="grid-col grid-border" style="--i: 4">
        <img src="/res/img/xiaren.gif" alt="" />
      </div>
      <div class="grid-col grid-border" style="--i: 5">
        <img src="/res/img/tieniu.gif" alt="" />
      </div>
      <div class="grid-col grid-noBg" style="--i: 6">
        <img src="/res/svg/douyin.svg" alt="" />
      </div>
    </div>
    <div class="grid">
      <div
        class="grid-col"
        style="grid-column: 1 / span 2; grid-row: 1 / span 3"
      ></div>
      <div
        class="grid-col"
        style="
          display: flex;
          grid-column: 3 / span 2;
          grid-row: 1 / span 1;
          color: #000;
          font-size: 12px;
        "
      >
        <div style="font-weight: bolder; font-size: 18px">{{ timer.ww }}</div>
        <div>{{ timer.HH }}:</div>
        <div>{{ timer.mm }}:</div>
        <div>{{ timer.ss }}</div>
      </div>
      <div
        class="grid-col"
        style="grid-column: 3 / span 1; grid-row: 2 / span 1"
      >
        <Icon>
          <template #default>🍘</template>
          <template #fill>🍚</template>
        </Icon>
      </div>
    </div>
    <div class="grid">
      <div
        class="grid-col"
        style="grid-column: 1 / span 7; grid-row: 1 / span 2"
      ></div>
      <div
        class="grid-col"
        style="grid-column: 1 / span 7; grid-row: 3 / span 1"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Icon from '@/components/animation/icon/index.tsx'
import { ref } from 'vue'
const cls = ref('')
let weekdays = ['日', '一', '二', '三', '四', '五', '六']
const getHHmm = (count: number = 0) => {
  let time = new Date()

  return {
    HH: time.getHours(),
    mm: String(time.getMinutes()).padStart(2, '0'),
    ss: String(time.getSeconds()).padStart(2, '0'),
    ww: weekdays[time.getDay()],
    count
  }
}
const timer = ref(getHHmm())
let count = 0
setInterval(() => {
  count++
  timer.value = getHHmm(count % 2)
}, 1000)
</script>

<style lang="scss">
img {
  display: block;
  width: 100%;
  height: 100%;
}
.container {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(4, 1fr);
}
.grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  grid-template-rows: repeat(3, 1fr);
  width: 360px;
  height: 160px;
  background: seagreen;
  padding: 10px;
  gap: 10px;
  border-radius: 4px;
  user-select: none;
  &-col {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #fff;
    border-radius: 4px;
    color: #fff;
    overflow: clip;
    cursor: pointer;
  }
  &-main {
    grid-column: 1 / span 2;
    grid-row: 1 / span 2;
  }
  &-banner {
    position: relative;
    grid-column: 3 / span 5;
    grid-row: 1 / span 2;
    background: #000;
    color: #4caf50;
  }
  &-icon {
    img {
      width: 80%;
    }
  }
  &-border {
    border: 2px solid #fff;
  }
  &-noBg {
    background: none;
  }
}
.text {
  text-align: center;
  font-size: 32px;
  font-weight: bold;
}
</style>
