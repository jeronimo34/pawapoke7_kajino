<template>
  <div id="game-container" @click="click()">
    <BackGround></BackGround>
    <GameBoard ref="gameboard"></GameBoard>
    <ButtonContainer
      :btnEnable="state === 2"
      :number="targetNumber"
      @selectBigOrLittle="selectBigOrLittle"
    ></ButtonContainer>
    <SpeechBubble :text="text"></SpeechBubble>
    <DaiceBoard ref="daiceBoard" :number="targetNumber"></DaiceBoard>
    <Girl></Girl>
    <PawapokeKun></PawapokeKun>
    <Win ref="win"></Win>
    <Confirmation
      @selectYes="continueGame(true)"
      @selectNo="continueGame(false)"
      ref="confirmation"
    ></Confirmation>
  </div>
</template>

<script>
import BackGround from "./BackGround.vue";
import GameBoard from "./GameBoard.vue";
import ButtonContainer from "./ButtonContainer.vue";
import SpeechBubble from "./SpeechBubble.vue";
import DaiceBoard from "./DaiceBoard.vue";
import Girl from "./Girl.vue";
import PawapokeKun from "./PawapokeKun.vue";
import Win from "./Win.vue";
import Confirmation from "./Confirmation.vue";

export default {
  components: {
    BackGround,
    GameBoard,
    ButtonContainer,
    SpeechBubble,
    Girl,
    DaiceBoard,
    PawapokeKun,
    Win,
    Confirmation,
  },
  data: function () {
    return {
      text: "いらっしゃいませ!",
      state: 1,
      targetNumber: -1,
      bigOrLittle: 0,
    };
  },
  mounted: function () {
    this.targetNumber = getRandomInt(4, 17);
    this.$refs.gameboard.setNGNumber(this.targetNumber);
  },
  methods: {
    continueGame: function (val) {
      if (val === true) {
        this.$refs.gameboard.clearNGNumbers();
        this.targetNumber = getRandomInt(4, 17);
        this.$refs.gameboard.setNGNumber(this.targetNumber);
        this.state = 10;
        this.text = "いらっしゃいませ!";
      } else {
        this.$refs.gameboard.clearNGNumbers();
        this.targetNumber = getRandomInt(4, 17);
        this.$refs.gameboard.setNGNumber(this.targetNumber);
        this.state = 11;
        this.text = "帰れ!";
      }
    },
    selectBigOrLittle: function (bigOrLittle) {
      // alert(bigOrLittle);
      this.bigOrLittle = bigOrLittle;
      this.state = 3;
      if (bigOrLittle === 1) {
        this.text = "大ね？ それではいきます!";
        this.$refs.gameboard.setNGNumbers(this.targetNumber, 1);
      } else {
        this.text = "小ね？ それではいきます!";
        this.$refs.gameboard.setNGNumbers(this.targetNumber, 0);
      }
    },
    click: function () {
      // state
      // SelectBigOrLittle
      //
      let state = this.state;

      if (state === 0) {
        this.text = "いらっしゃいませ!";
        this.state = 1;
      } else if (state === 1) {
        this.text = "大小 どちらにいたしますか?";
        this.state = 2;
      } else if (state === 3) {
        // 大、小の選択待ち
        this.state = 4;
      } else if (state === 4) {
        // 大が選択された
        // 横から「開始」の文字がフェードイン
        // this.text = "開始";
        this.$refs.win.showStartText();

        setTimeout(() => {
          this.$refs.win.hideAll();
          this.state = 5;
          this.$refs.daiceBoard.startDaice();
        }, 1500);
      } else if (state === 5) {
        //daice1
        this.$refs.daiceBoard.stopDaice();

        this.state = 6;
      } else if (state === 6) {
        //daice2
        this.$refs.daiceBoard.stopDaice();
        this.state = 7;
      } else if (state === 7) {
        //daice3
        this.$refs.daiceBoard.stopDaice();
        let result = this.$refs.daiceBoard.getDaiceResult();
        this.$refs.gameboard.setResultNumber(result);

        console.log(result);

        if (this.bigOrLittle === 1) {
          if (result > this.targetNumber) {
            this.text = "成功";
            this.$refs.win.showWinText();
          } else {
            this.text = "失敗";
            this.$refs.win.showLoseText();
          }
        } else {
          if (result < this.targetNumber) {
            this.text = "成功";
            this.$refs.win.showWinText();
          } else {
            this.text = "失敗";
            this.$refs.win.showLoseText();
          }
        }
        this.state = 8;
      } else if (state === 8) {
        this.$refs.win.hideAll();
        this.text = "まだ続ける?";
        this.$refs.confirmation.toggle(true);
        // 確認ダイアログを出す
        this.state = 9;
      } else if (state === 9) {
        // this.text = "はいが選択された。";
        // setTimeout(() => {
        //   // 初期化
        //   this.$refs.gameboard.clearNGNumbers();
        //   this.targetNumber = getRandomInt(4, 17);
        //   this.$refs.gameboard.setNGNumber(this.targetNumber);
        //   this.state = 1;
        //   this.text = "いらっしゃいませ!";
        // }, 1000);
      } else if (state === 10) {
        this.state = 1;
      } else {
        this.state = -1;
      }
    },
  },
};

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min) + min); //The maximum is exclusive and the minimum is inclusive
}
</script>

<style scoped>
#game-container {
  width: 480px;
  height: 320px;
  position: relative;
}
</style>
