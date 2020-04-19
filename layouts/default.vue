<template>
  <div>
    <nuxt />
  </div>
</template>

<script>
export default {};
</script>

<style>
body {
  padding: 20px 30px;
}
.page-enter-active,
.page-leave-active {
  transition: opacity 0.3s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>