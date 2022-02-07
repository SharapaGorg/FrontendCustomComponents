<template>
  <div>
    <side-bar :positions="positions" class="float-left"/>
    <div class="float-left" style="width : calc(100vw - 300px)">
      <nuxt style="margin-top : 45vh" class="mx-auto"/>
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
