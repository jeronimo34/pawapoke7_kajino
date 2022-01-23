<template>
  <div id="speech-bubble">
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Body",
    };
  },
  props: ["text"],
};
</script>

<style scoped>
#speech-bubble {
  position: absolute;
  left: 0px;
  top: 184px;
}

#speech-bubble p {
  position: absolute;
  background: white;
  top: -5px;
  left: 30px;
  font-size: 24px;
  width: 320px;
  height: 36px;
}
</style>
