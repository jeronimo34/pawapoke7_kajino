<template>
  <div id="daice-board">
    <img src="@/assets/DaiceBoard.png" />
    <!-- <div class="daice"></div> -->
    <!-- <span>{{ daiceNumbers }}</span> -->
    <div
      v-if="daiceShows[0]"
      v-bind:style="styleObject[0]"
      class="daice"
      id="daice1"
    ></div>
    <div
      v-if="daiceShows[1]"
      v-bind:style="styleObject[1]"
      class="daice"
      id="daice2"
    ></div>
    <div
      v-if="daiceShows[2]"
      v-bind:style="styleObject[2]"
      class="daice"
      id="daice3"
    ></div>

    <!-- <img v-bind:style="styleObject" src="@/assets/daice1_6.png" /> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      intervalids: ["", "", ""],
      daiceNumbers: [1, 1, 1],
      daiceShows: [false, false, false],
      currentDaiceIdx: 0,
      //オブジェクトデータをインラインスタイルで適用
      styleObject: [
        {
          backgroundPositionX: "0px",
          backgroundPositionY: "0px",
        },
        {
          backgroundPositionX: "0px",
          backgroundPositionY: "0px",
        },
        {
          backgroundPositionX: "0px",
          backgroundPositionY: "0px",
        },
      ],
    };
  },
  mounted: function () {
    //this.startDaice();
    // setInterval(() => {
    //   console.log("update");
    //   this.styleObject.backgroundPosition = 64 * this.daiceNumbers[0] + "px";
    // }, 1000);
  },
  beforeUnmount() {
    for (let i = 0; i < 3; ++i) clearInterval(this.intervalids[i]);
  },
  methods: {
    clearAll: function () {
      for (let i = 0; i < 3; ++i) {
        this.styleObject[i].backgroundPositionY = "0px";
        this.styleObject[i].backgroundPositionX = "0px";
        this.daiceShows[i] = false;
      }
    },
    startDaice: function () {
      this.currentDaiceIdx = 0;
      for (let i = 0; i < 3; ++i) {
        this.daiceShows[i] = true;
        this.intervalids[i] = setInterval(
          function () {
            this.daiceNumbers[i]++;
            if (this.daiceNumbers[i] > 6) this.daiceNumbers[i] = 1;

            this.styleObject[i].backgroundPositionX =
              64 * this.daiceNumbers[i] + "px";
          }.bind(this),
          50
        );
      }
    },
    stopDaice: function () {
      if (this.intervalids[this.currentDaiceIdx]) {
        clearInterval(this.intervalids[this.currentDaiceIdx]);
        this.styleObject[this.currentDaiceIdx].backgroundPositionY = 64 + "px";
        this.currentDaiceIdx++;
      }
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
  background: url("~@/assets/daice1_6.png") repeat;
  width: 64px;
  height: 64px;
  position: absolute;
  /* animation: smile 0.25s steps(6) infinite;
  display: none; */
}

#daice-board {
  position: relative;
  left: 88px;
  top: 272px;
}
#daice1 {
  /* animation: daice1 1s linear forwards; */
  animation: daice1 0.75s linear forwards;
}
@keyframes daice1 {
  0% {
    left: -128px;
    top: -200px;
  }
  80% {
    left: 0px;
    top: -24px;
  }
  100% {
    left: 22px;
    top: -24px;
  }
}

#daice2 {
  /* animation: daice1 1s linear forwards; */
  animation: daice2 0.75s linear forwards;
}
@keyframes daice2 {
  0% {
    left: -128px;
    top: -200px;
  }
  80% {
    left: 70px;
    top: -24px;
  }
  100% {
    left: 92px;
    top: -24px;
  }
}
#daice3 {
  /* animation: daice1 1s linear forwards; */
  animation: daice3 0.75s linear forwards;
}

@keyframes daice3 {
  0% {
    left: -128px;
    top: -200px;
  }
  80% {
    left: 140px;
    top: -24px;
  }
  100% {
    left: 160px;
    top: -24px;
  }
}
/* #daice-board > span {
  position: absolute;
  top: 10px;
  left: 10px;
} */
</style>
