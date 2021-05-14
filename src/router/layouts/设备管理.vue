<script>
import appConfig from '@src/app.config'
import Layout from '@layouts/main.vue'

export default {
  page: {
    title: 'Home',
    meta: [{ name: 'description', content: appConfig.description }],
  },
  components: { Layout },
}
</script>

<template>
  <Layout>
    <div style="display: flex;padding: 10px">
      <img id="u229_img" class="img " src="http://iot.flsiot.com:202/pub/images/框架/u229.png" tabindex="0" style="cursor:pointer; outline: none;margin-left:10px;width: 15px;height: 15px">
      <div style="display: grid; margin-left: 10px">
        <span style="text-decoration:none;">无人值守场站管理系统</span>
        <span style="text-decoration:none;">Unattended Charging Station Platform</span>
      </div>
    </div>
    <iframe :class="$style.container" id="u247_input" data-label="首页内部框架" scrolling="auto" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" src="http://iot.flsiot.com:202/pub/设备列表.html"></iframe>
  </Layout>
</template>

<style lang="scss" module>
@import '@design';

.container {
  flex: 1;
}
</style>
