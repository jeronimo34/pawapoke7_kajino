<template>
  <div class="ichimatsu"></div>
</template>

<script>
export default {};
</script>

<style scoped>
@keyframes bg-scrolling {
  0% {
    background-position: 100% 100%;
  }
  100% {
    background-position: 0% 0%;
  }
}

.ichimatsu {
  position: absolute;
  width: 480px;
  height: 320px;
  background-repeat: repeat;
  background: url("~@/assets/BackGround.png");
  animation: bg-scrolling linear 30s infinite;
}
</style>
