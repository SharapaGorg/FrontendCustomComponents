<template>
  <div>
    <div class="submit-button" @click="submit" ref="root">
      <span>{{ buttonMessage }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubmitButton",
  data() {
    return {
      buttonMessage : 'Submit me',
    }
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
      }, 500)

    }
  }
}
</script>

<style scoped>

.submit-button {
  background: #1243e7;
  color: #EEF0F4;
  width: 135px;
  transition: all .5s ease;
  margin-top: 40vh;
  @apply px-7 py-2 mx-auto cursor-pointer text-center;
}

.submit-button:hover {
  border-radius: 15px;
}

</style>
