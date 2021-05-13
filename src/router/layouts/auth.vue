
<template>
  <div :class="$style.container">
    <slot />
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
</style>
