<template>
  <div class="homepage">
      <div class="bg-color-storm-container">
        <div class="bg-color-storm">
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
        </div>
      </div>

      <div class="title">
          邮卫兵
      </div>
      <div class="subtitle">
          祝北邮人永远健康!
      </div>
  </div>
</template>

<script setup lang="ts">

</script>

<style scoped>
.homepage {
    position: relative;
    width: 100%;
    height: 100%;
    background-position: center center;
    background-repeat: no-repeat;
    background-color: black;
    overflow: hidden;
    display: flex;
}

.title {
    position: absolute;
    color: white;
    text-align: center;
    top: 40%;
    left: 50%;
    transform: translateX(-50%);
    font-size: 4vi;
    font-weight: bold;
}

.subtitle {
    position: absolute;
    color: white;
    text-align: center;
    top: 52%;
    left: 50%;
    transform: translateX(-50%);
    font-size: 1.2vi;
}

.bg-color-storm-container {
    /*position: absolute;*/
    width: 100%;
    height: 100%;
    display: flex;
    /*align-items: center;*/
    justify-content: center;
}

.bg-color-storm {
    width: 30em;
    height: 30em;
    font-size: 30px;
    color: lime;
    display: flex;
    align-items: center;
    justify-content: center;
    animation: change-color 10s linear infinite;
    opacity: 20%;
}

@keyframes change-color {
    to {
        filter: hue-rotate(1turn);
    }
}

.bg-color-storm span {
    position: absolute;
    --diameter: calc(5em + (var(--n) - 1) * 3em);
    width: var(--diameter);
    height: var(--diameter);
    border-style: solid;
    border-width: 1em 1em 0 0;
    border-color: currentColor transparent;
    border-radius: 50%;
    animation: rotating linear infinite;
    animation-duration: calc(10s / (9 - var(--n) + 1));
}

@keyframes rotating {
    to {
        transform: rotate(1turn);
    }
}

.bg-color-storm span:nth-child(1) {
    --n: 1;
}

.bg-color-storm span:nth-child(2) {
    --n: 2;
}

.bg-color-storm span:nth-child(3) {
    --n: 3;
}

.bg-color-storm span:nth-child(4) {
    --n: 4;
}

.bg-color-storm span:nth-child(5) {
    --n: 5;
}

.bg-color-storm span:nth-child(6) {
    --n: 6;
}

.bg-color-storm span:nth-child(7) {
    --n: 7;
}

.bg-color-storm span:nth-child(8) {
    --n: 8;
}

.bg-color-storm span:nth-child(9) {
    --n: 9;
}

</style>
