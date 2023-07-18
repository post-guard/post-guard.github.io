<template>
    <div class="evaluate-page">
        <div class="evaluate-page-title" ref="evaluate_page_title">
<!--            他们选择了邮卫兵-->
        </div>
        <div class="evaluate-list">
          <el-card class="evaluate-card evaluate-card-1"
                   :body-style="{ padding: '0px' }">

              <img src=public/usersFace/Ayaka.jpg>

              <div class="evaluation">
                  神里
              </div>
          </el-card>
        </div>
    </div>
</template>

<script setup lang="ts">


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

.evaluate-page-title {
    margin: 5% auto 95% auto;
    font-size: 2vi;
    opacity: 1;
    color: cornflowerblue;
    transition: all 1s ease;
    width: auto;
    height: auto;
}

.evaluate-list {
    position: absolute;
    width: 100%;
    height: 90%;
    top: 10%;
}

.evaluate-card {
    width: 25%;
    overflow: hidden;
    transition: all 1s ease;
}

.evaluate-card:hover {
    filter: blur(2px) brightness(50%);
}
</style>
