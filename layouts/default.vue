<template>
  <div>
    <side-bar :positions="positions" class="float-left"/>
    <div class="float-left" style="width : calc(100vw - 300px); height : 100vh; overflow : hidden">
      <nuxt/>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      positions: [
        {
          title: 'Dynamic navigator',
          route: 'DynamicNavigatorRoute'
        },
        {
          title : 'Start button',
          route: 'StartButtonRoute'
        },
        {
          title : 'Submit button',
          route : 'SubmitButtonRoute'
        }
      ]
    }
  },
}
</script>


<style>
body, html {
  background-color: #EE5180;
}
</style>
