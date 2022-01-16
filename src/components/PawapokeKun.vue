<template>
  <div v-bind:style="this.styleObject" id="pawapoke-kun"></div>
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
#pawapoke-kun {
  background: url("~@/assets/PawapokeKun.png") repeat;
  width: 80px;
  height: 80px;
  position: absolute;
  left: 330px;
  top: 240px;
}
</style>
