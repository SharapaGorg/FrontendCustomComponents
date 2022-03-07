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
          title: 'Form',
          route : 'FormRoute'
        },
        {
          title : 'Clock',
          route : 'ClockRoute'
        },
        {
          title : 'Track',
          route: 'TrackRoute'
        }
      ]
    }
  },
}
</script>


<style>
body, html {
  background-color: #7086c2;
}
</style>
