<template>
    <div class="vision-page">
        <div class="vision-page-main-part">
            <div class="vision-page-title">
                我们的愿景
            </div>
            <div class="vision-page-content">

                「让全北邮人不挂科,不延毕;
                <br>
                &emsp;&emsp;&emsp;
                让这个世界变得更加可爱」
            </div>
            <div class="vision-page-history-title">
                我们的脚步
            </div>
            <div class="vision-page-history-content">

                <p>北京邮电大学邮卫兵团队。</p>

                <del>当然也可以叫我们邮小将。</del>

                <p>面对大二的大作业危机，二次元、原批、小黑子集合在一起，
                    <del>决定成为学院偶像。</del>
                </p>

                <p>你说得对，但是《大作业》是由北京邮电大学非自主研发的一款陈旧封闭世界冒险游戏。
                    <br>
                    游戏发生在一个被称作“吸土城”的现实世界，在这里，选中“设计课”的人将被授予“IDE”，导引代码之力。
                    <br>
                    你将扮演一位名为“菜鸡”的神秘角色，在屎山的堆砌过程中邂逅表现各异，能力独特的Bugs，将她们一一修好，找回失散的学分
                    <br>
                    同时，逐步发掘“自来卷”的真相。</p>

            </div>
        </div>
    </div>
</template>

<script setup lang="ts">

</script>

<style scoped>
.vision-page {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    padding: 0;
    margin: 0;
    background-color: #f6fafe;
}

.vision-page-main-part {
    position: absolute;
    left: 0;
    top: 15%;
    width: 100%;
    height: 85%;
    /*text-align: center;*/
}

.vision-page-title {
    position: relative;
    color: #4a5151;
    font-size: 1.5rem;
    font-weight: bold;
    left: 20%;
}


@keyframes gradientAnimation {
    0% {
        background-position: 0 0;
    }
    100% {
        background-position: 100% 100%;
    }
}


.vision-page-content {
    position: relative;
    font-size: 2.5rem;
    font-weight: lighter;
    letter-spacing: 0.25rem;
    top: 5%;
    text-align: center;
    background-image: linear-gradient(to right, #64beff, #4b91ff, #c9a0ff, #a945ff, #4b91ff, #64beff);
    background-size: 500% 250%;;
    color: transparent;
    -webkit-background-clip: text;
    animation: gradientAnimation 8s ease infinite;
}

.vision-page-history-title {
    position: relative;
    color: #4a5151;
    font-size: 1.5rem;
    font-weight: bold;
    top: 15%;
    left: 20%;
}

.vision-page-history-content {
    position: relative;
    font-size: 1rem;
    font-weight: normal;
    top: 18%;
    left: 20%;
    color: black;

}
</style>
