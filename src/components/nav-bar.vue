<script>
import { authComputed } from '@state/helpers'
import NavBarRoutes from './nav-bar-routes.vue'

export default {
  components: { NavBarRoutes },
  data() {
    return {
      tab1: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u113.svg',
          name: '场站可视化',
          title: '场站可视化',
        },
      ],
      tab2: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u79.svg',
          name: '场站管理',
          title: '场站管理',
        },
      ],
      tab3: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u86.svg',
          name: '运维人员管理',
          title: '运维人员管理',
        },
      ],
      tab4: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u93.svg',
          name: '设备管理',
          title: '设备管理',
        },
      ],
      tab5: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u100.svg',
          name: '实时报警',
          title: '实时报警',
        },
      ],
      tab6: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u106.svg',
          name: '历史报警',
          title: '历史报警',
        },
      ],
      tab7: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u121.svg',
          name: '角色管理',
          title: '角色管理',
        },
      ],
      tab8: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u133.svg',
          name: '用户管理',
          title: '用户管理',
        },
      ],
      tab9: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u141.svg',
          name: '数据字典',
          title: '数据字典',
        },
      ],
      tab10: [
        {
          icon: 'http://iot.flsiot.com:202/pub/images/框架/u146.svg',
          name: '操作日志',
          title: '操作日志',
        },
      ],
      persistentNavRoutes: [
        {
          name: 'home',
          title: '历史报警',
        },
      ],
      loggedInNavRoutes: [
        {
          name: 'profile',
          title: () => 'Logged in as ' + this.currentUser.name,
        },
        {
          name: 'logout',
          title: 'Log out',
        },
      ],
      loggedOutNavRoutes: [
        {
          name: 'logout',
          title: 'Log out',
        },
      ],
    }
  },
  computed: {
    ...authComputed,
  },
}
</script>

<template>
  <ul :class="$style.container">
    <div style="cursor:pointer;display: flex;justify-content: center;align-items: center;">
      <img style="width: 30px; height: 30px" id="u69_img" class="img " src="http://iot.flsiot.com:202/pub/images/框架/u68.svg">
      <p style="font-size: 24px">场站管理</p>
    </div>
    <NavBarRoutes :routes="tab1" />
    <p>场站管理</p>
    <NavBarRoutes :routes="tab2" />
    <NavBarRoutes :routes="tab3" />
    <NavBarRoutes :routes="tab4" />
    <p>报警管理</p>
    <NavBarRoutes :routes="tab5" />
    <NavBarRoutes :routes="tab6" />
    <p>系统设置</p>
    <NavBarRoutes :routes="tab7" />
    <NavBarRoutes :routes="tab8" />
    <NavBarRoutes :routes="tab9" />
    <NavBarRoutes :routes="tab10" />
    <!--    <NavBarRoutes :routes="persistentNavRoutes" />-->
<!--    <NavBarRoutes v-if="loggedIn" :routes="loggedInNavRoutes" />-->
    <NavBarRoutes :routes="loggedOutNavRoutes" />
  </ul>
</template>

<style lang="scss" module>
@import '@design';

.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 256px;
  font-size: 14px;
  margin: 0;
  padding: 0;

  p {
    font-size: 18px;
    color: #FFFFFF;
    margin-left: 10px;
  }

  > li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px 24px;
    cursor: pointer;

    > div {
      display: flex;
      align-items: center;

      img {
        margin-right: 8px;
      }

      span {
        line-height: 1;
        color: white;
      }
    }

    > img {
      width: 16px;
      height: 16px;
    }
  }
}
</style>
