<template>
<div class="superiority-page">
    <div class="superiority-page-title" ref="superiority_page_title">
        为什么选择我们?
    </div>
    <div class="reason-list">
        <el-row>

        </el-row>
    </div>
</div>
</template>

<script setup lang="ts">
import {onMounted, ref, watch} from "vue";

const superiority_page_title = ref<HTMLElement>();

const props = defineProps<{
    currentPage:number;
    pageNumber:number;
}>()

onMounted(()=>{

    watch(() => props.currentPage,(newVal, oldVal)=> {

        if ("style" in superiority_page_title.value) {
            if (newVal == props.pageNumber) {
                // 监听是否进入本页面,为页面元素的出现特效的最终位置做准备
                superiority_page_title.value.style.marginTop = "5%";
                superiority_page_title.value.style.marginBottom = "95%";
                superiority_page_title.value.style.opacity = 1;
            } else {
                // 监听是否不在本页面,为页面元素的出现特效的初始位置做准备
                if (newVal < props.pageNumber) {
                    // 此时的页面在本页面的上面
                    superiority_page_title.value.style.marginTop = "10%";
                    superiority_page_title.value.style.marginBottom = "90%";
                    superiority_page_title.value.style.opacity = 0;
                } else if (newVal > props.pageNumber) {
                    // 此时的页面在本页面的下面
                    superiority_page_title.value.style.marginTop = "0";
                    superiority_page_title.value.style.marginBottom = "100%";
                    superiority_page_title.value.style.opacity = 0;
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
    background-image: repeating-linear-gradient(0deg, #fdfdfd, #fdfdfd 20px,#fff 20px, #fff 40px);

}

.superiority-page-title {
    margin: 10% auto 90% auto;
    font-size: 2vi;
    opacity: 0;
    color: cornflowerblue;
    transition: all 1s ease;
}

</style>
