<template >
  <div>
    <div id="footer">Made with Nuxt + Typescript</div>
  </div>
</template>
<script>
import Vue from "vue";

export default Vue.extend({
  name: "Footer",
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
