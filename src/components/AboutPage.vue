<template>
  <!--  <p>北京邮电大学邮卫兵团队。</p>

    <del>当然也可以叫我们邮小将。</del>

    <p>面对大二的大作业危机，二次元、原批、小黑子集合在一起， <del>决定成为学院偶像。</del></p>

    <p>你说得对，但是《大作业》是由北京邮电大学非自主研发的一款陈旧封闭世界冒险游戏。
      游戏发生在一个被称作“吸土城”的现实世界，在这里，选中“设计课”的人将被授予“IDE”，导引代码之力。
      你将扮演一位名为“菜鸡”的神秘角色，在屎山的堆砌过程中邂逅表现各异，能力独特的Bugs，将她们一一修好，找回失散的学分——
      同时，逐步发掘“自来卷”的真相。</p>-->

    <div class="about-page">
        <div class="about-page-title">
            团队成员
        </div>

        <div class="about-page-content">
            <div class = "about-page-wave">

            </div>
            <el-row class="about-page-member" justify="space-evenly">
                <template v-for="member in memberList" :key="member">
                    <el-col :span="24/memberList.length">
                        <div class="about-page-member-single">
                            <el-avatar
                                    class="about-page-member-single-avatar"
                                    :src = member.avatar
                                    :size=250
                                    :fit="'cover'"
                            />
                            <div class="about-page-member-single-name">
                                {{member.name}}
                            </div>
                            <div class="about-page-member-single-introduce">
                                {{member.introduce}}
                            </div>
                            <div class="about-page-member-single-dialog">
                                {{member.dialog}}
                            </div>
                        </div>
                    </el-col>
                </template>

            </el-row>
        </div>
    </div>


</template>

<script setup lang="ts">
import {ref} from "vue";

const memberList = ref(
    [{
            avatar:"usersFace/Ayaka.jpg",
            name: "ichirinko",
            introduce: "乐子人",
            dialog: "新佛曰：諸隸僧皤降吽諸陀摩隸僧皤缽皤薩嚤皤斯咒皤諦皤伏僧諸嘚皤僧皤吽吶嘇羅陀皤嚩空咤愍皤缽摩若嚤菩諦皤祗陀陀皤須皤嘚嚤所哆嘇祗哆僧嘇若隸皤宣嚴咤降空皤愍嚴吶哆嘚彌咒心皤若如如囑皤"
        },
        {
            avatar:"usersFace/Ayaka.jpg",
            name: "rrricardo",
            introduce: "void",
            dialog: "void"
        },
        {
            avatar:"usersFace/Ayaka.jpg",
            name: "Lan_G",
            introduce: "void",
            dialog: "void"
        }
    ]);
</script>

<style scoped>

.about-page {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    padding: 0;
    margin: 0;
}

.about-page-title {
    position: absolute;
    top: 10%;
    left: 50%;
    transform: translateX(-50%);
    font-size: 2em;
    opacity: 1;
    color: cornflowerblue;
    transition: all 1s ease;
}

.about-page-content {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translateX(-50%);
    width :80%;
    height: 70%;
    opacity: 1;

}

.about-page-member {
    height: 100%;
    justify-content: center;
}

.about-page-member-single {
    height: 90%;
    padding: 5% 10% 5% 10%;
    text-align: center;
    overflow: hidden;
}

.about-page-member-single-avatar {
    margin: auto;
}

.about-page-wave {
    position: absolute;
    top: 18%;
    left: 50%;
    transform: translateX(-50%);
    width: 180em;
    height: 150em;
    border-radius: 50% 50%;
    background-color: #87c2fc;
}

.about-page-member-single-name {
    color: white;
    font-size: 2em;
    font-family: "Comic Sans MS", "FounderType Straw-cloked Man", ui-monospace;
    padding: 0.5em;
}

.about-page-member-single-introduce {
    color: white;
    font-size: 1.4em;
    font-family: "Comic Sans MS", "FounderType Straw-cloked Man", ui-monospace;
    padding: 0.5em;
}

.about-page-member-single-dialog {
    color: white;
    font-size: 1.2em;
    font-family: "Comic Sans MS", "FounderType Straw-cloked Man", ui-monospace;
    padding: 0.5em;
    overflow: hidden;
}
</style>
