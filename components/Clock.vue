<template>
  <div ref="root">
    <div class="clock">
      <img class="w-full h-full background absolute" alt=""/>
        <div class="clock-center"></div>
        <div class="second-arrow" ref="secondArrow"></div>
        <div class="minute-arrow" ref="minuteArrow"></div>
        <div class="hour-arrow"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Clock",
  data() {
    return {
      currentSecondRotation : 0,
      currentMinuteRotation: 0
    }
  },
  methods: {
    rotateSecondArrow() {
      this.$refs.secondArrow.style.transform = `rotateZ(${this.currentSecondRotation + 360}deg)`
      this.currentSecondRotation += 360
    },
    rotateMinuteArrow() {
      this.$refs.minuteArrow.style.transform = `rotateZ(${this.currentMinuteRotation + 360}deg)`
      this.currentMinuteRotation += 360
    }
  },
  mounted() {
    // seconds
    setTimeout(() => {
        this.rotateSecondArrow()
    }, 0)

    setInterval(() => {
        this.rotateSecondArrow()
    }, 60 * 1000)

    //minutes
    setTimeout(() => {
      this.rotateMinuteArrow()
    }, 0)

    setTimeout(() => {
      this.rotateMinuteArrow()
    }, 60 * 60 * 1000)
  },
}
</script>

<style scoped>

.clock {
  @apply rounded-[100%] h-[600px] w-[600px] mx-auto border-4 border-black bg-transparent/20 backdrop-filter backdrop-blur-lg overflow-hidden
}

.background {
  filter : blur(2px);
  /*background : url("https://i.gifer.com/LrMw.gif") center;*/
}

.clock-center {
  margin-top: calc(50% - 15px);
  @apply w-[30px] h-[30px] rounded-[100%] bg-black relative mx-auto
}

.second-arrow {
  transition : all 60s ease;
  background: linear-gradient(to left, black 50%, transparent 50%);
  @apply w-[550px] h-[4px] ml-[21px] relative bottom-[15px]
}

.minute-arrow {
  transition : all 3600s ease;
  background: linear-gradient(to left, black 50%, transparent 50%);
  @apply w-[440px] h-[4px] ml-[76px] relative bottom-[19px]
}

</style>
