<template>
  <div id="gameboard">
    <Prize
      v-for="(prize, index) in prizes"
      :key="index"
      :x="prize.x"
      :y="prize.y"
      :ng="prize.ng"
      :choosed="prize.choosed"
      :number="prize.number"
      :delay="80 * index"
    ></Prize>
    <img src="@/assets/GameBoard.png" />
  </div>
</template>

<script>
import Prize from "./Prize.vue";

export default {
  components: {
    Prize,
  },
  data() {
    return {
      prizes: [
        {
          x: 8,
          y: 16,
          number: 3,
          ng: false,
          choosed: false,
        },
        {
          x: 56,
          y: 16,
          number: 4,
          ng: false,
          choosed: false,
        },
        {
          x: 104,
          y: 16,
          number: 5,
          ng: false,
          choosed: false,
        },
        {
          x: 152,
          y: 16,
          number: 6,
          ng: false,
          choosed: false,
        },
        {
          x: 200,
          y: 16,
          number: 7,
          ng: false,
          choosed: false,
        },
        {
          x: 248,
          y: 16,
          number: 8,
          ng: false,
          choosed: false,
        },
        {
          x: 296,
          y: 16,
          number: 9,
          ng: false,
          choosed: false,
        },
        {
          x: 344,
          y: 16,
          number: 10,
          ng: false,
          choosed: false,
        },
        {
          x: 8,
          y: 96,
          number: 11,
          ng: false,
          choosed: false,
        },
        {
          x: 56,
          y: 96,
          number: 12,
          ng: false,
          choosed: false,
        },
        {
          x: 104,
          y: 96,
          number: 13,
          ng: false,
          choosed: false,
        },
        {
          x: 152,
          y: 96,
          number: 14,
          ng: false,
          choosed: false,
        },
        {
          x: 200,
          y: 96,
          number: 15,
          ng: false,
          choosed: false,
        },
        {
          x: 248,
          y: 96,
          number: 16,
          ng: false,
          choosed: false,
        },
        {
          x: 296,
          y: 96,
          number: 17,
          ng: false,
          choosed: false,
        },
        {
          x: 344,
          y: 96,
          number: 18,
          ng: false,
          choosed: false,
        },
      ],
    };
  },
  methods: {
    setResultNumber: function (result) {
      for (let i = 0; i < this.prizes.length; ++i) {
        let prize = this.prizes[i];
        if (prize.number === result) {
          prize.choosed = true;
        }
      }
    },
    clearNGNumbers: function () {
      for (let i = 0; i < this.prizes.length; ++i) {
        this.prizes[i].ng = false;
        this.prizes[i].choosed = false;
      }
    },
    // NG番号セット
    setNGNumber: function (targetNumber) {
      this.prizes[targetNumber - 3].ng = true;
    },
    // 中心値以下、または、以上の数字の色を赤に変更
    setNGNumbers: function (targetNumber, bigOrLittle) {
      if (bigOrLittle === 1) {
        for (let i = 0; i < this.prizes.length; ++i) {
          let prize = this.prizes[i];
          if (prize.number <= targetNumber) {
            prize.ng = true;
          }
        }
      } else {
        for (let i = 0; i < this.prizes.length; ++i) {
          let prize = this.prizes[i];
          if (prize.number >= targetNumber) {
            prize.ng = true;
          }
        }
      }
    },
  },
};
</script>

<style scoped>
#gameboard {
  position: absolute;
  left: 0px;
  top: 8px;
}
</style>
