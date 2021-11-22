<template>
  <div class = 'navigator' ref = 'navigator'></div>
</template>

<script>
export default {
  name: "DynamicNavigator",
  data() {
    return {
        activateItems : false
    }
  },
  mounted() {
    let navigator = this.$refs.navigator

    navigator.onclick = () => {
      console.log(1);
    }
  }
}
</script>

<style scoped>

.navigator {
  height: 50px;
  width: 50px;
  background-color: #50c878;
  border-radius: 50%;
  display: inline-block;
  box-shadow: 0 3px 2px #574D4D;
  transition : .5s;
}

.navigator:hover {
  box-shadow: 0 10px 15px #574D4D;
  border: 1px dashed #EE5180;
}

</style>
