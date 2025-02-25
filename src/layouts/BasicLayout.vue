<template>
  <div id="basiclayouts">
    <a-layout style="min-height: 100vh">
      <a-layout-header class="header">
        <GlobalHeader />
      </a-layout-header>
      <a-layout-content class="content">
        <router-view />
      </a-layout-content>
      <a-layout-footer class="footer">这是一个OJ系统</a-layout-footer>
    </a-layout>
  </div>
</template>

<style scoped>
#basiclayouts {
}

#basiclayouts .content {
  background: linear-gradient(to right, #fefefe, #fff);
  margin-bottom: 16px;
  padding: 20px;
}

#basiclayouts .header {
  margin-bottom: 16px;
  box-shadow: #eee 1px 1px 5px;
}

#basiclayouts .footer {
  background: #efefef;
  padding: 16px;
  position: sticky;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
}
</style>
<script setup lang="ts">
import GlobalHeader from "@/components/GlobalHeader.vue";
</script>
