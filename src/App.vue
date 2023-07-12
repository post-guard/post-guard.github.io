<template>
  <div class="post-guard-layout">
    <el-container class="post-guard-el-container">
        <el-header class="post-guard-el-header">
            Post Guard
        </el-header>
        <el-main class="post-guard-el-main">
            <div class="section section1">
                1
            </div>
            <div class="section section2">
                2
            </div>
            <div class="section section3">
                3
            </div>
            <div class="section section4">
                4
            </div>
        </el-main>
<!--        <el-footer class="post-guard-el-footer">
            Foot
        </el-footer>-->
    </el-container>
  </div>
</template>

<script setup lang="ts">
import {ref} from "vue";

ref pageController<> : {
    currentPage : 1;
    isScrolling : false;
    deltaY : 0;
}

function move(index) {

}

</script>



<style scoped>
.post-guard-layout {
    position:absolute;
    top:0;
    right:0;
    bottom:0;
    left:0;
}

.post-guard-el-container {
    height: 100vh;
    transition: all linear 0.5s;
}

.post-guard-el-header {
    height: 5vh;
}

.post-guard-el-main {
    height: 95vh;
    padding: 0;
    overflow: hidden;
}

.post-guard-el-footer {
    height: 5vh;
}

.section {
    width: 100%;
    height: 100%;
    background-position: center center;
    background-repeat: no-repeat;
}

.section1 {
    background-color: rgb(129, 227, 116);
}
.section2 {
     background-color: rgb(227, 197, 116);
 }
.section3 {
    background-color: rgb(116, 144, 227);
}
.section4 {
    background-color: rgb(216, 116, 227);
}

</style>
