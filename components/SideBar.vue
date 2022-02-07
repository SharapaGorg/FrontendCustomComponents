<template>
  <div class="sidebar">
    <div class="sidebar__title"> Elements</div>
    <div
      v-for="position in positions"
      class="position"
      :style='{ background :  (selectedComponent === position.title) ? "gray" : ""}'
      @click="selectComponent(position)"
    >
      {{ position.title }}
    </div>

  </div>
</template>

<script>
export default {
  name: "SideBar",
  props: ['positions'],
  data() {
    return {
      selectedComponent: ''
    }
  },
  methods: {
    selectComponent(position) {
      this.selectedComponent = position.title;
      this.$router.push(position.route)
    }
  }
}
</script>

<style scoped>

.sidebar {
  width: 300px;
  height: 100vh;
  color: #EEF0F4;
  background: #403939;
}

.sidebar__title {
  padding: 10px;
  font-size: 24px;
  border-bottom: 1px solid gray;
  @apply mx-auto;
}

.position {
  padding: 5px 15px;
  width: 300px;
  cursor: pointer;
}

.position:hover {
  background: gray;
}

</style>
