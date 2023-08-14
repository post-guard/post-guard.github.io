<template>
  <div class="evaluate-page" id="evaluate-page">
    <div class="evaluate-part">
      <div class="evaluate-dialog" @wheel.stop>
        <div class="evaluate-dialog-main" ref="evaluate_dialog_main" >
          <!--                    {{ evaluateList[currentEvaluate].dialog }}-->
          <div v-html="evaluateList[currentEvaluate].dialog" ></div>
        </div>
        <div class="evaluate-dialog-name" ref="evaluate_dialog_name">
          {{ evaluateList[currentEvaluate].name }}
        </div>
      </div>
      <el-carousel
          :interval="0"
          type="card"
          height="200px"
          indicator-position="none"
          @change="(newVal)=>changeEvaluate(newVal)"
          style="
                top: 80%;
                text-align: center;
                justify-content: center;
                width: 30%">
<!--这里完全可以使用循环吧，，，，，-->
        <el-carousel-item class="evaluate-avatar avatar0">
          <el-avatar
              :size=100
              :fit="'cover'"
              :src=evaluateList[0].avatar
          />
        </el-carousel-item>
        <el-carousel-item class="evaluate-avatar avatar1">
          <el-avatar
              :size=100
              :fit="'cover'"
              :src=evaluateList[1].avatar
          />
        </el-carousel-item>
        <el-carousel-item class="evaluate-avatar avatar2">
          <el-avatar
              :size=100
              :fit="'cover'"
              :src=evaluateList[2].avatar
          />
        </el-carousel-item>
        <el-carousel-item class="evaluate-avatar avatar3">
          <el-avatar
              :size=100
              :fit="'cover'"
              :src=evaluateList[3].avatar
          />
        </el-carousel-item>
        <el-carousel-item class="evaluate-avatar avatar4">
          <el-avatar
              :size=100
              :fit="'cover'"
              :src=evaluateList[4].avatar
          />
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script setup lang="ts">
import {onMounted, ref} from "vue";
import createRibbons from "@/components/coloredRibbonEvanYou";
import '/src/assets/font/font.css'

const evaluate_dialog_main = ref<HTMLElement>();
const evaluate_dialog_name = ref<HTMLElement>();

const currentEvaluate = ref(0);
const evaluateList = ref([
  {
    // 这里放邮卫兵组织的logo
    avatar: "usersFace/Ayaka.jpg",
    name: "邮卫兵组织召开新闻发布会",
    dialog:
        "上学期，面对艰巨繁重的各项实践课程大作业开发任务，邮卫兵小组紧急成立，临危受命，坚决贯彻落实邮卫兵组织成立大会上全体成员的各项" +
        "决策部署，坚持稳中求进的工作主基调，更好的统筹学习专业基础知识和提升自身开发水平两个大局，为各位参加同学本学期的绩点稳中向好发展" +
        "注入了新的动力。 <br>" +
        "初步统计，上学期邮卫兵团队共合作开发大小项目<b>5个</b>，其中实践课程的大作业占60%，课程实验占40%。从开发技术上来看，使用Springboot和Vue.js" +
        "前后端分离技术开发的网页项目一个，使用Springboot和JavaFX前后端分离开发的客户端项目一个，使用C语言开发的项目一个，使用Electron和Vue.js" +
        "等新式技术开发的客户端项目一个，使用Java开发的命令行程序一个。从代码数量上看，小组使用Vue.js等网站相关技术编写代码<b>14116行</b>，使用Java" +
        "等技术编写代码<b>21852行</b>，使用C等技术编写代码<b>3923行</b>。<br>" +
        "总的来看，上一学期，邮卫兵小组以全体小组都选修Java为抓手，锻炼了各位小组同学面向对象设计和开发的能力，提高了各位小组同学的自学能力，" +
        "高质量完成了上一学期的所有课程实验和课程大作业。同时也需要看到在开发过程中暴露的各种问题：各位同学对于基础的编程知识仍不熟练，缺少" +
        "使用各种编程工具提高开发效率的功能，在代码风格上存在诸多不足。下一步，各位参加同学仍要以完成各项课程实验和课程大作业为契机，磨炼" +
        "开发技巧，在实践中提升自己对于计算机系统的了解和掌握。对于目前仍然存在缺陷的方面，遵循“调整、巩固、恢复、提高”的八字方针，补短板、强弱项。" +
        "对于目前取得了一定成就的领域，要戒骄戒躁，争取获得更大的进步，实现个人能力的有效增长和个人成绩和合理提升。"
  },
  {
    avatar: "usersFace/Ayaka.jpg",
    name: "神里绫华",
    dialog: "分别至今,我依然会不时想起你。最近我新发现一条小径,花开时遍地都是粉色，从那里还能看到烟火，附近又有小吃铺子…等你有时间,我想请你去逛逛。\n" +
        "\n" +
        "                    此刻你应该正在为重要的事奔波吧?每一天都向着目标前进,每一步都比前一步更踏实…正因如此,才能达成目标。\n" +
        "\n" +
        "                    世上一定存在着只有你能做到的事。我也是如此,站在自己的位置上，做好每一件分内事。\n" +
        "\n" +
        "                    还请不要太劳累了,照顾好自己和派蒙。另外,有个不情之请…\n" +
        "\n" +
        "                    或许有些任性,但唯有今天。希望能见你一面。\n" +
        "\n" +
        "                    若不嫌弃,就请于今夜到樱树下与我相见吧。这个时节,月光非常美丽…愿有幸与你一同欣赏。"
  },
  {
    avatar: "usersFace/Ayaka.jpg",
    name: "知名港台记者 射命丸文",
    dialog: "大学作业这回事，自己就不可以预料。一个人的命运啊，当然要靠自我奋斗，但是也要考虑到历史的行程。" +
        "我绝对不知道，我作为一个普通大学生，作业怎么就这么难，所以邮小将同志出现了，说“我们都决定啦，你来试用我们的产品”，我说另请高明吧。\n" +
        "我实在也不是谦虚，我一个大学生怎么能用邮卫兵了呢？" +
        "但是呢，邮小将同志讲“大家已经研究决定了”，所以后来我就念了两首诗，叫“苟利国家生死以，岂因祸福避趋之”，" +
        "没想到我是too young too simple, sometimes naive，这个邮卫兵的产品，真是比其他代写不知道高到哪里去了!"
  },
  {
    avatar: "usersFace/114514.png",
    name: "24岁学生 田所浩二",
    dialog: "那么首先能告诉我你的年龄吗？" + '<br>' +
        "是24岁" + '<br>' +
        "24岁，已经工作了吗？ " + '<br>' +
        "是学生" + '<br>' +
        "学生、啊（轻蔑）" + '<br>' +
        "那么身高体重是多少呢？" + '<br>' +
        "身高是170公分，体重是74公斤" + '<br>' +
        "74。。。有在做什么运动吗？我看你好像还挺结实的" + '<br>' +
        "倒是没有特别在做什么，不过有在健身" + '<br>' +
        "有作业吗现在" + '<br>' +
        "现在没有" + '<br>' +
        "啊、现在没有。。。那，几时写完的呢？" + '<br>' +
        "去、去年吧。。。（心虚）" + '<br>' +
        "有用过邮卫兵的产品吗？" + '<br>' +
        "曾经用过" + '<br>' +
        "比较喜欢哪个产品呢？" + '<br>' +
        "说的也是呢。。。。果然我还是王道征途，泡泡系吧（指邮简的聊天气泡）" + '<br>' +
        "啊、泡泡系？很贵的吧，那个" + '<br>' +
        "有的还好吧。。。" + '<br>' +
        "那么推荐邮卫兵什么的有在搞吧？" + '<br>' +
        "这个可以有！（赞赏）" + '<br>' +
        "哦、有吗？ " + '<br>' +
        "有有有 " + '<br>' +
        "呃，那每周多少次呢？还是说。。。" + '<br>' +
        "嗯。。。不知道有多少次啦，反正还挺频繁的、在向他人推荐" + '<br>' +
        "那么、呃。。。最近，什么时候推荐的？" + '<br>' +
        "最近就，三天前吧" + '<br>' +
        "啊。。。三天前啊" + '<br>' +
        "最后有什么想说的吗？" + '<br>' +
        "一一试，无疑是，已久依旧霸一领" + '<br>' +
        "(试过一个又一个产品，邮卫兵无疑是最好的，已经用了这么久了，它依旧霸占第一的绝对领导地位)"
  },
  {
    avatar: "usersFace/ricardo.png",
    name: "邮卫兵技术负责人 Ricardo",
    dialog:
        "问：到目前为止，邮卫兵的具体技术是怎么样的呢？ <br>" +
        "答：技术，我们邮卫兵组织发展的历史还比较短，学业上的压力还很重。 <br>" +
        "问：那到目前为止，邮卫兵的具体技术是怎么样的呢？ <br>" +
        "答：我们邮卫兵小组坚持实施卓越工程师培养计划，在学习计算机科学相关基础知识的过程中呢，要提高成员的编程水平，对接当前市面上技术的发展水平，" +
        "搞好实践课程教学。 <br>" +
        "问：现在的技术水平情况怎么样呢？ <br>" +
        "答：。。。 <br>" +
        "问：从2021年入学到现在技术水平提高了多少？ <br>" +
        "答：。。。 <br>" +
        "问：邮卫兵小组的一些项目，运行起来平均20分钟就要报段错误退出，占用内存在10G以上。" +
        "作为邮卫兵的技术负责人，你对于这样的项目，你有什么看法呢？ <br>" +
        "答：我说不出来。"
  }
])

onMounted(() => {
  createRibbons({
    display: "block",
    horizontalSpeed: 150,
    colorCycleSpeed: 1,
    ribbonCount: 3,
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
    id: "bgCanvas3",
    container: "evaluate-page"
  })
})

function changeEvaluate(newVal: number) {

  setTimeout(() => {
    if ("style" in evaluate_dialog_main.value) {
      evaluate_dialog_main.value.style.opacity = 0;
    }
    if ("style" in evaluate_dialog_name.value) {
      evaluate_dialog_name.value.style.opacity = 0;
    }
  }, 0);

  setTimeout(() => {
    if ("style" in evaluate_dialog_main.value) {
      evaluate_dialog_main.value.style.opacity = 1;
    }
    if ("style" in evaluate_dialog_name.value) {
      evaluate_dialog_name.value.style.opacity = 1;
    }
    currentEvaluate.value = newVal;
  }, 200);
}

</script>

<style scoped>
.evaluate-page {
  background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAwAAAAMCAYAAABWdVznAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAACFJREFUeNpiZGBg4GegAsBlCD8TqSYNQg2Mo6FEBAAIMACdPABtrSW/IQAAAABJRU5ErkJggg==") repeat fixed;
  -webkit-font-smoothing: antialiased;
  text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.04);
  min-height: 100%;
  margin: 0;
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.evaluate-part {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;

}

.evaluate-avatar:not(.is-in-stage) {
  opacity: 0;
}

.evaluate-avatar {
  transition: all ease-in-out 0.4s;
}

.evaluate-dialog {
  position: absolute;
  border-radius: 5em;
  width: 60%;
  height: 60%;
  top: 10%;
  border: 1em double #409eff;
  background-color: rgb(255, 255, 255);
  box-shadow: 5px 5px 0 0 #409EFFFF;
}

.evaluate-dialog::after {
  content: '';
  width: 2em;
  height: 2em;
  border-radius: 0.5em;
  border-bottom: 1em double #409eff;
  border-right: 1em double #409eff;
  background-color: white;
  position: absolute;
  bottom: -2.2em;
  left: 50%;
  z-index: 2;
  transform: translateX(-50%) rotate(45deg);
  transform-origin: center;

}

.evaluate-dialog-main {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 10%;
  width: 96%;
  height: 75%;
  background-color: #2098D100;
  font-size: 1.5em;
  color: #409eff;
  line-height: 175%;
  font-family: "Comic Sans MS", "FounderType Straw-cloked Man", ui-monospace;
  overflow-x: hidden;
  overflow-y: auto;
  text-align: justify;
  transition: opacity linear 0.2s;
  padding-right: 1%;
  padding-left: 1%;
}


.evaluate-dialog-main::-webkit-scrollbar { /*滚动条整体样式*/
  width: 10px;
  height: 1px;
}

.evaluate-dialog-main::-webkit-scrollbar-thumb { /*滚动条里面小方块*/
  border-radius: 10px;
  -webkit-box-shadow: inset 0 0 5px rgba(103, 115, 192, 0.2);
  background: #409eff;
}

.evaluate-dialog-main::-webkit-scrollbar-track { /*滚动条里面轨道*/
  -webkit-box-shadow: inset 0 0 5px rgba(189, 66, 66, 0.2);
  border-radius: 10px;
  background: #87c2fc;
}


.evaluate-dialog-name {
  position: absolute;
  right: 5%;
  top: 85%;
  width: auto;
  height: 15%;
  background-color: #2098D100;
  font-size: 1.8em;
  color: #409eff;
  line-height: 175%;
  font-family: "Comic Sans MS", "FounderType Straw-cloked Man", ui-monospace;
  overflow-x: hidden;
  overflow-y: auto;
  text-align: justify;
  transition: opacity linear 0.2s;
}
</style>
