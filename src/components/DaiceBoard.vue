<template>
  <div id="daice-board">
    <img src="@/assets/DaiceBoard.png" />
    <div class="daice"></div>
    <span>{{ daiceNumbers }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      intervalids: ["", "", ""],
      daiceNumbers: [1, 1, 1],
      currentDaiceIdx: 0,
    };
  },
  mounted: function () {
    //this.startDaice();
  },
  beforeUnmount() {
    for (let i = 0; i < 3; ++i) clearInterval(this.intervalids[i]);
  },
  methods: {
    startDaice: function () {
      this.currentDaiceIdx = 0;
      for (let i = 0; i < 3; ++i) {
        this.intervalids[i] = setInterval(
          function () {
            this.daiceNumbers[i]++;
            if (this.daiceNumbers[i] > 6) this.daiceNumbers[i] = 1;
          }.bind(this),
          50
        );
      }
    },
    stopDaice: function () {
      clearInterval(this.intervalids[this.currentDaiceIdx]);
      this.currentDaiceIdx++;
    },
    getDaiceResult: function () {
      let sum = 0;
      this.daiceNumbers.forEach((x) => {
        sum += x;
      });
      return sum;
    },
    isDone: function () {
      console.log("is done");
    },
  },
};
</script>

<style scoped>
.daice {
  background: url("~@/assets/daice1_6.png") no-repeat;
  width: 64px;
  height: 64px;
  animation: smile 0.25s steps(6) infinite;
  display: none;
}
@keyframes smile {
  to {
    background-position: -384px 0;
  }
}
#daice-board {
  position: relative;
  left: 88px;
  top: 272px;
}
#daice-board > span {
  position: absolute;
  top: 10px;
  left: 10px;
}
</style>
