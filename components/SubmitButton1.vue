<template>
  <div>
    <div class="submit-button" @click="submit" ref="root">
      <span>{{ buttonMessage }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubmitButton1",
  data() {
    return {
      buttonMessage: 'Submit me',
      defaultAnimationDuration: 500
    }
  },
  props: {
    clickAnimation: String,
    animationDuration: Number
  },
  methods: {
    submit() {
      const button = this.$refs.root;
      const duration = this.animationDuration ? this.animationDuration : this.defaultAnimationDuration
      this.buttonMessage = '. . .'

      button.style.width = '77px'

      setTimeout(() => {
        button.style.width = '135px'

        setTimeout(() => {
          this.buttonMessage = 'Submit me'
        }, 500)

      }, duration * 10)
    }
  }
}
</script>

<style scoped>

</style>
