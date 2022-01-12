<template>
  <div>
    <div id="win" v-if="showWin">
      <img id="win1" src="@/assets/win1.png" />
      <img id="win2" src="@/assets/win2.png" />
      <img id="win3" src="@/assets/win3.png" />
    </div>
    <div id="win" v-if="showLose">
      <img id="win1" src="@/assets/lose1.png" />
      <img id="win2" src="@/assets/lose2.png" />
      <img id="win3" src="@/assets/lose3.png" />
    </div>
    <div id="win" v-if="showStart">
      <img id="start" src="@/assets/start.png" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showWin: false,
      showLose: false,
      showStart: false,
    };
  },
  methods: {
    showWinText: function () {
      this.showWin = true;
    },
    showLoseText: function () {
      this.showLose = true;
    },
    showStartText: function () {
      this.showStart = true;
    },
    hideAll: function () {
      this.showWin = false;
      this.showLose = false;
      this.showStart = false;
    },
  },
};
</script>
<style scoped>
#win {
  position: absolute;
  top: 108px;
}
#win1 {
  position: absolute;
  animation: fadeIn 1s;
  animation-fill-mode: forwards;
}
#win2 {
  position: absolute;
  animation: fadeIn2 1s;
  animation-fill-mode: forwards;
}
#win3 {
  position: absolute;
  animation: fadeIn3 1s;
  animation-fill-mode: forwards;
}
#start {
  position: absolute;
  animation: fadeInStart 1s;
  animation-fill-mode: forwards;
}
@keyframes fadeIn {
  0% {
    transform: translateX(-128px);
  }
  100% {
    transform: translateX(0px);
  }
}

@keyframes fadeIn2 {
  0% {
    transform: translateX(-128px);
  }
  100% {
    transform: translateX(128px);
  }
}

@keyframes fadeIn3 {
  0% {
    transform: translateX(-128px);
  }
  100% {
    transform: translateX(256px);
  }
}

@keyframes fadeInStart {
  0% {
    transform: translateX(-128px);
  }
  100% {
    transform: translateX(128px);
  }
}
</style>
