<template>
  <div id="button-container">
    <img src="@/assets/ButtonContainer.png" />
    <button id="big-btn" v-bind:disabled="!btnEnable" v-on:click="selectBig">
      大
    </button>
    <span id="target-number">{{ number }}</span>
    <button
      id="little-btn"
      v-bind:disabled="!btnEnable"
      v-on:click="selectLittle"
    >
      小
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      enable: true,
    };
  },
  methods: {
    // 大選択
    selectBig: function () {
      //alert("大が選択された");
      this.$emit("selectBigOrLittle", 1);
    },
    // 小選択
    selectLittle: function () {
      //alert("小が選択された");
      this.$emit("selectBigOrLittle", 0);
    },
    // 数字決めロジック
    desideNumber: function () {
      alert("数字が決まった");
    },
  },
  props: ["btnEnable", "number"],
};
</script>

<style scoped>
#button-container {
  position: absolute;
  left: 400px;
  top: 8px;
}
#big-btn {
  position: absolute;
  left: 10px;
  top: 28px;
  width: 56px;
  height: 56px;
}
#little-btn {
  position: absolute;
  left: 10px;
  top: 188px;
  width: 56px;
  height: 56px;
}
#target-number {
  position: absolute;
  left: 10px;
  top: 108px;
  width: 56px;
  height: 56px;
  text-align: center;
  background: white;
}
</style>
