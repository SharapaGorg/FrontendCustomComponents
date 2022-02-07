<template>
  <div class="mx-auto" style="width : fit-content">
    <div ref="blue" class="blue__container">
      <div ref="red" class="red__container">
        <div ref="green" class="green__container">
          <div class="start-button" ref="root" @click="activate">Click me</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StartButton",
  methods: {
    activate() {
        this.$refs.green.style.padding = '200px'

        setTimeout(() => {
            this.$refs.red.style.padding = '200px'
        }, 1000)

        setTimeout(() => {
            this.$refs.blue.style.padding = '200px'
        }, 2000)
    }
  }
}
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Supermercado+One&display=swap');

.start-button {
  width : fit-content;
  background : #1243e7;
  color: #EEF0F4;
  border-radius: 15px;
  font-family: 'Supermercado One', cursive;
  @apply px-6 py-1 cursor-pointer;
}

.green__container {
  background : green;
  width : fit-content;
  border-radius: 50%;
  transition: .5s all ease;
}

.red__container {
  background : red;
  width : fit-content;
  border-radius: 50%;
  transition : .5s all ease;
}

.blue__container {
  background : blue;
  width : fit-content;
  border-radius: 50%;
  transition: .5s all ease;
}

</style>
