<script>
import NavBar from '@components/nav-bar.vue'

const savedCurrentUser = JSON.parse(
  window.localStorage.getItem('auth.currentUser')
)
export default {
  components: savedCurrentUser && { NavBar },
}
</script>

<template>
  <div :class="$style.container">
    <NavBar />

    <div :class="$style['main-content']">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" module>
@import '@design';

.container {
  display: flex;
  min-width: 100%;
  min-height: 100%;
  margin: 0 auto;
}
.main-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  background: white;
}
</style>
