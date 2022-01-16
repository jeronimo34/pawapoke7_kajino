<template>
  <div v-bind:style="this.styleObject" id="girl"></div>
</template>

<script>
export default {
  data() {
    return {
      imageIndex: 0,
    };
  },
  mounted: function () {},
  methods: {},
  watch: {},
  computed: {
    styleObject: function () {
      let styleObject = {};
      styleObject.backgroundPositionX = this.imageIndex * 80 + "px";
      return styleObject;
    },
  },
};
</script>

<style scoped>
#girl {
  background: url("~@/assets/Girl.png") repeat;
  width: 80px;
  height: 80px;
  position: absolute;
  left: 8px;
  top: 240px;
}
</style>
