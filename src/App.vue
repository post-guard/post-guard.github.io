<template>
    <div class="post-guard-layout" ref="post_guard_layout">
        <el-container class="post-guard-el-container"
                      ref="post_guard_el_container"
                      @mousewheel="mouseWheelHandle"
                      @DOMMouseScroll="mouseWheelHandle">
            <el-header class="post-guard-el-header">
                Post Guard
            </el-header>
            <el-main class="post-guard-el-main" ref="post_guard_el_main">
                <div class="sectionController" ref="sectionController">
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
                </div>

            </el-main>
<!--            <el-footer class="post-guard-el-footer">
                Foot
            </el-footer>-->
        </el-container>
    </div>
</template>

<script setup lang="ts">
import {onMounted, ref} from "vue";

const post_guard_layout = ref<HTMLElement>();
const post_guard_el_container = ref<HTMLElement>();
const post_guard_el_main = ref<HTMLElement>();
const sectionController = ref<HTMLElement>();

const pageController = ref({
    currentPage: 1,
    pageSum: 4,
    isScrolling: false,
    deltaY: 0,
})

function move(index) {

        pageController.value.isScrolling = true;

        let height = sectionController.value.clientHeight; //获取屏幕的高度
        let scrollHeight; // 计算滚动判断是往上滚还往下滚

        scrollHeight = -(index - 1) * height + "px";
        sectionController.value.style.transform = `translateY(${scrollHeight})`;
        pageController.value.currentPage = index;

        setTimeout(() => {
            pageController.value.isScrolling = false;
        }, 800);

}

// 往下切换
function nextPage() {
    if (pageController.value.currentPage + 1 <= pageController.value.pageSum) { // 如果当前页面编号+1 小于总个数，则可以执行向下滑动
        pageController.value.currentPage += 1; // 页面+1
        move(pageController.value.currentPage); // 执行切换
    }
}

// 往上切换
function previousPage() {
    if (pageController.value.currentPage - 1 > 0) { // 如果当前页面编号-1 大于0，则可以执行向上滑动
        pageController.value.currentPage -= 1; // 页面-1
        move(pageController.value.currentPage); // 执行切换
    }
}

function mouseWheelHandle(event) {
    // 添加冒泡阻止
    let evt = event;
    if (evt.stopPropagation) {
        evt.stopPropagation();
    } else {
        evt.returnValue = false;
    }
    if (pageController.value.isScrolling) { // 判断是否可以滚动
        return false;
    }
    let e = event;
    pageController.value.deltaY = e.deltaY || e.detail; // Firefox使用detail
    if (pageController.value.deltaY > 0) {
        nextPage();
    } else if (pageController.value.deltaY < 0) {
        previousPage();
    }
}
</script>


<style scoped>
.post-guard-layout {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}

.post-guard-el-container {
    height: 100vh;

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

.sectionController {
    height: inherit;
    transition: all linear 0.5s;
}

</style>
