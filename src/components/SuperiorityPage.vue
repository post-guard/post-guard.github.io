<template>
    <div class="superiority-page" id="superiority-page">
        <div class="superiority-page-title" ref="superiority_page_title">
            为什么选择我们?
        </div>
        <div class="reason-list" ref="reason_list">
            <el-row
                    style="position:absolute; top:10%;width: 100%;margin: auto 0  auto 0">
                <el-col :span="12">
                    <div class="reason reason1">
                        <div class="reason reason1 title">
                            为北邮人而生
                        </div>

                        <div class="underline-from-center">
                            <div class="reason reason1 content">
                                大作业也不太可能跨校合作吧（应该
                            </div>
                        </div>
                    </div>
                </el-col>
                <el-col :span="12">
                    <div class="reason reason2">
                        <div class="reason reason2 title">
                            提供高质量产品
                        </div>
                        <div class="underline-from-center">
                            <div class="reason reason2 content">
                                完善的代码注释、详尽的自述文件 <br>
                                让您开箱即用
                            </div>
                        </div>
                    </div>
                </el-col>
            </el-row>

            <el-row
                    style="position:absolute; top:50%;width: 100%;margin: auto 0  auto 0">
                <el-col :span="12">
                    <div class="reason reason3">
                        <div class="reason reason3 title">
                            流行的技术框架
                        </div>

                        <div class="underline-from-center">
                            <div class="reason reason3 content">
                                Springboot, Electron, Vue.js
                            </div>
                        </div>
                    </div>
                </el-col>
                <el-col :span="12">
                    <div class="reason reason4">
                        <div class="reason reason4 title">
                            多渠道后续支持
                        </div>
                        <div class="underline-from-center">
                            <div class="reason reason4 content">
                                可以通过电子邮件、issue等方式同我们激情对线 <br>
                                亦可以直接线下当面battle
                            </div>
                        </div>
                    </div>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script setup lang="ts">
import {onMounted, ref, watch} from "vue";
import createRibbons from './coloredRibbonEvanYou'

const superiority_page_title = ref<HTMLElement>();
const reason_list = ref<HTMLElement>();

const props = defineProps<{
    currentPage: number;
    pageNumber: number;
}>()

onMounted(() => {
    createRibbons({
        display: "block",
        horizontalSpeed: 150,
        colorCycleSpeed: 5,
        ribbonCount: 4,
        colorAlpha: 0.65,
        strokeSize: 0,
        margin: "auto",
        padding: "0",
        border: "0",
        position: {type: "absolute", top: '0', bottom: '0', left: '0', right: '0'},
        width: "100%",
        height: "100%",
        z_index: "-1",
        color: "#E4EFF000",
        id: "bgCanvas2",
        container: "superiority-page"
    })

    watch(() => props.currentPage, (newVal, oldVal) => {

        if ("style" in superiority_page_title.value && "style" in reason_list.value) {
            if (newVal == props.pageNumber) {
                // 监听是否进入本页面,为页面元素的出现特效的最终位置做准备
                superiority_page_title.value.style.marginTop = "5%";
                superiority_page_title.value.style.marginBottom = "95%";
                superiority_page_title.value.style.opacity = 1;

                reason_list.value.style.top = "30%";
                reason_list.value.style.opacity = 1;

            } else {
                // 监听是否不在本页面,为页面元素的出现特效的初始位置做准备
                if (newVal < props.pageNumber) {
                    // 此时的页面在本页面的上面
                    superiority_page_title.value.style.marginTop = "10%";
                    superiority_page_title.value.style.marginBottom = "90%";
                    superiority_page_title.value.style.opacity = 0;

                    reason_list.value.style.top = "40%";
                    reason_list.value.style.opacity = 0;
                } else if (newVal > props.pageNumber) {
                    // 此时的页面在本页面的下面
                    superiority_page_title.value.style.marginTop = "0";
                    superiority_page_title.value.style.marginBottom = "100%";
                    superiority_page_title.value.style.opacity = 0;

                    reason_list.value.style.top = "20%";
                    reason_list.value.style.opacity = 0;
                }
            }
        }
    })
})


</script>

<style scoped>
.superiority-page {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    background-image: repeating-linear-gradient(0deg, #fdfdfdcc, #fdfdfdcc 20px, #ffffffaa 20px, #ffffffaa 40px);
    padding: 0;
    margin: 0;
}

.superiority-page-title {
    margin: 10% auto 90% auto;
    font-size: 2vi;
    opacity: 0;
    color: cornflowerblue;
    transition: all 1s ease;
}

.reason-list {
    display: flex;
    position: absolute;
    top: 30%;
    left: 50%;
    width: 100%;
    height: 70%;
    transform: translateX(-50%);
    align-content: center;
    transition: all 1s ease;
}

.reason {
    align-content: center;
    text-align: center;
}

.title {
    color: cornflowerblue;
    font-size: 1.4vi;
}

.content {

    width: 100%;
    font-size: 1.2vi;
}


/* Underline From Center */
.underline-from-center {
    display: inline-block;
    vertical-align: middle;
    text-align: center;
    transform: perspective(1px) translateZ(0);
    box-shadow: 0 0 1px rgba(0, 0, 0, 0);
    position: relative;
    overflow: hidden;
    padding: 5% 0 0 0;
}

.underline-from-center:before {
    content: "";
    position: absolute;
    z-index: -1;
    left: 51%;
    right: 51%;
    bottom: 0;
    background: #2098D1;
    height: 4px;
    transition-property: left, right;
    transition-duration: 0.3s;
    transition-timing-function: ease-out;
}

.underline-from-center:hover:before, .underline-from-center:focus:before, .underline-from-center:active:before {
    left: 0;
    right: 0;
}
</style>
