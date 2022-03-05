<template>
  <div>
    <div class="status">DEV</div>
    <div class="trigger-button" ref="activateButton" @click="triggerAll">{{ message }}</div>
    <div class="grid grid-cols-3 justify-items-center">
      <submit-button/>
      <submit-button1/>
    </div>
  </div>
</template>

<script>

export default {
  name: "SubmitButtonRoute",
  data() {
    return {
      message : 'Activate all'
    }
  },
  methods: {
    triggerAll() {
      this.$refs.activateButton.style.boxShadow = 'inset 20px 20px 60px #ca456d,inset -20px -20px 60px #ff5d93';
      this.$emit('force')
      this.message = 'Triggered'

      setTimeout(() => {
        this.$refs.activateButton.style.boxShadow = '20px 20px 60px #ca456d'
        this.message = 'Activate all'
      }, 5000)
    }
  }
}
</script>

<style scoped>

</style>
