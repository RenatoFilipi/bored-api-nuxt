<template >
  <div>
    <div id="footer">{{ text }}</div>
  </div>
</template>
<script>
import Vue from "vue";

export default Vue.extend({
  name: "Footer",
  props: {
    text: ""
  },
});
</script>
<style>
#footer {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 7vh;
  background-color: #32475b;
  color: #fff;
}
</style>
