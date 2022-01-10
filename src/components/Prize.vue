<template>
  <div
    class="fadeIn"
    v-if="show"
    id="prize"
    v-bind:style="{ left: x + 'px', top: y + 'px' }"
    v-bind:class="{ fadeIn: show }"
  >
    <img src="@/assets/Prize.png" />
    <span v-bind:class="{ ng: ng, zoom: choosed }">{{ number }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: 0,
      show: false,
    };
  },
  props: ["x", "y", "number", "delay", "ng", "choosed"],
  mounted() {
    setTimeout(() => {
      this.show = true;
    }, this.delay);
  },
};
</script>

<style scoped>
.ng {
  color: red;
}
#prize {
  position: relative;
}
#prize > img {
  position: absolute;
}
#prize > span {
  position: absolute;
  background: white;
  width: 24px;
  left: 14px;
  top: 48px;
  text-align: center;
}
.fadeIn {
  animation-name: fadeInAnime;
  animation-duration: 0.2s;
  animation-fill-mode: forwards;
  opacity: 0;
}
@keyframes fadeInAnime {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.zoom {
  animation-name: zoom;
  animation-iteration-count: infinite;
  animation-duration: 0.3s;
  animation-direction: alternate;
  transform: scale(1);

  animation-fill-mode: forwards;
}
@keyframes zoom {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.2);
  }
}
</style>
