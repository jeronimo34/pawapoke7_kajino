<template>
  <div>
    <GameContainer></GameContainer>
    <!-- <div>
      <button v-on:click="show = !show">Toggle</button>
      <transition name="fade">
        <p>hello</p>
      </transition>
    </div> -->
  </div>
</template>

<script>
import GameContainer from "./components/GameContainer.vue";

export default {
  components: {
    GameContainer,
  },
};
// export default {
//   data() {
//     return {
//       show: false,
//     };
//   },
// };
</script>

<style scoped>
#prize {
  position: absolute;
}

#prize > img {
  position: absolute;
}
#prize > span {
  position: absolute;
  background: white;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
