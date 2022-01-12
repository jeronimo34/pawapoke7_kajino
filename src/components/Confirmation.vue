<template>
  <div id="confirmation" v-if="show">
    <span id="yes" v-on:click="selectYes">はい</span>
    <span id="no" v-on:click="selectNo">いいえ</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
    };
  },
  methods: {
    selectYes: function () {
      this.$emit("selectYes");
    },
    selectNo: function () {
      this.$emit("selectNo");
    },
    toggle(val) {
      this.show = val;
    },
  },
};
</script>
<style scoped>
#confirmation {
  position: absolute;
  top: 204px;
  left: 216px;
  width: 160px;
  height: 32px;
  background: white;
}
#yes {
  /* position: absolute;
  top: 204px;
  left: 228px; */
  font-size: 24px;
}
#no {
  /* position: absolute;
  top: 204px;
  left: 308px; */
  font-size: 24px;
  padding-left: 10px;
}
</style>
