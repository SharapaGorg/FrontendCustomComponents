<template>
  <div>
    <div class="submit-button" @click="submit" ref="root" @force="submit">
      <span>{{ buttonMessage }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubmitButton",
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
      this.buttonMessage = '. . .'
      let counter = 0

      let timer = setInterval(() => {
        let even = counter % 2 === 1
        counter++

        button.style.webkitBorderBottomRightRadius = even ? '20px' : ''
        button.style.webkitBorderTopLeftRadius = even ? '20px' : ''
        button.style.webkitBorderBottomLeftRadius = even ? '' : '20px'
        button.style.webkitBorderTopRightRadius = even ? '' : '20px'

        if (counter === 10) {
          button.style.borderRadius = ''

          this.buttonMessage = 'Submit me'

          clearInterval(timer);
        }
      }, this.animationDuration ? this.animationDuration : this.defaultAnimationDuration)

    },
    animation_2(button, counter) {
      button.style.width = '77px'

      setTimeout(() => {
        button.style.width = '135px'
        this.buttonMessage = 'Submit me'

      }, (this.animationDuration ? this.animationDuration : this.defaultAnimationDuration) * 10)
    }
  }
}
</script>
