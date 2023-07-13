<template>
    <div class="post-guard-layout" ref="post_guard_layout">
        <el-container class="post-guard-el-container"
                      ref="post_guard_el_container"
                      @mousewheel="mouseWheelHandle"
                      @DOMMouseScroll="mouseWheelHandle"
                      @touchstart="handleTouchstart"
                      @touchend="handleTouchend"
                      @touchmove="handleTouchmove">
            <el-header class="post-guard-el-header">
                <el-menu class="post-guard-el-menu"
                         ref="post_guard_el_menu"
                         mode="horizontal"
                         :default-active=pageController.currentPage.toString()
                         :ellipsis="false"
                         @select="(index)=>move(Number(index))"
                         >

                    <div class="flex-grow" style="flex-grow: 1"/>
                    <el-menu-item index="1">首页</el-menu-item>
                    <el-menu-item index="2">产品</el-menu-item>
                    <el-menu-item index="3">优势</el-menu-item>
                    <el-menu-item index="4">愿景</el-menu-item>
                    <el-menu-item index="5">用户评价</el-menu-item>
                    <el-menu-item index="6">我们</el-menu-item>
                </el-menu>
            </el-header>

            <el-main class="post-guard-el-main" ref="post_guard_el_main">
                <div class="sectionController" ref="sectionController">
                    <HomePage />
                    <div class="section section2">
                        2
                    </div>
                    <div class="section section3">
                        3
                    </div>
                    <div class="section section4">
                        4
                    </div>
                    <div class="section section5">
                        5
                    </div>
                    <div class="section section6">
                        6
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
import HomePage from "@/components/HomePage.vue";

const sectionController = ref<HTMLElement>();

const pageController = ref({
    currentPage: 1,
    pageSum: 6,
    isScrolling: false,
    deltaY: 0,
})

onMounted(()=>{
    menuSpecialization(1)
})
function move(index: number) {

        pageController.value.isScrolling = true;

        let height = sectionController.value?.clientHeight;
        // 获取屏幕的高度
        let scrollHeight;
        // 计算滚动判断是往上滚还往下滚

        scrollHeight = -(index - 1) * height + "px";
        menuSpecialization(index);


    if ("style" in sectionController.value) {
        sectionController.value.style.transform = `translateY(${scrollHeight})`;
    }


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


// 清除触摸事件
function handleTouchmove(event) {
    event.preventDefault()
}

// 手指按下屏幕
function handleTouchstart(event) {
    this.startTime = Date.now()
    this.startX = event.changedTouches[0].clientX
    this.startY = event.changedTouches[0].clientY
}

// 手指离开屏幕
function handleTouchend(event) {
    const endTime = Date.now()
    const endX = event.changedTouches[0].clientX
    const endY = event.changedTouches[0].clientY
    // 判断按下的时长
    if (endTime - this.startTime > 2000) {
        return;
    }
    // 滑动的方向
    let direction = "";
    // 先判断用户滑动的距离，是否合法，合法:判断滑动的方向 注意 距离要加上绝对值
    if (Math.abs(endY - this.startY) > 10) {
        //滑动方向
        direction = endY - this.startY > 0 ? "down" : "up"
    } else {
        return;
    }
    // 用户做了合法的滑动操作
    if (direction === 'up') {
        this.next();
    }
    if (direction === 'down') {
        this.pre();
    }
}


function menuSpecialization(index: number) {
        const menu = document.getElementsByClassName("post-guard-el-menu");
        console.log(menu.item(0))
        if (index == 1) {
                menu.item(0).setAttribute("style","height:10vh;"+
                    "--el-menu-bg-color: #000000;" +
                    "--el-menu-active-color: #ffffff;" +
                    "--el-menu-text-color: #606060;" +
                    "--el-menu-hover-text-color: #ffffff;" +
                    "--el-menu-hover-bg-color: #8e8e8e80;" +
                    "--el-menu-border-color: #000000");



        } else {
                menu.item(0).setAttribute("style","height:10vh;"+
                    "--el-menu-bg-color: #ffffff;" +
                    "--el-menu-active-color: #409eff;" +
                    "--el-menu-text-color: #000000;" +
                    "--el-menu-hover-text-color: #409eff;" +
                    "--el-menu-hover-bg-color: #ecf5ff;" +
                    "--el-menu-border-color: #ffffff");
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
    height: 10vh;
    padding: 0;

}

.post-guard-el-main {
    height: 100vh;
    padding: 0;
    overflow: hidden;
}

.post-guard-el-footer {
    /*height: 5vh;*/
}

.post-guard-el-menu {
    transition: all ease 0.5s;
}

.section {
    width: 100%;
    height: 100%;
    background-position: center center;
    background-repeat: no-repeat;
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

.section5 {
    background-color: rgb(0, 231, 255);
}

.section6 {
    background-color: rgb(227, 116, 160);
}

.sectionController {
    height: inherit;
    transition: all ease 0.5s;
}


/*::-webkit-scrollbar {
    width: 8px;
}
::-webkit-scrollbar-thumb {
    background-color: #eaecf1;
    border-radius: 3px;
}*/

</style>
