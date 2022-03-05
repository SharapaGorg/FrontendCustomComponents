<template>
  <div ref="root">
    <div class="form">
      <div class="h-[93%]">
        <span class="form-header">Log In</span>
        <div class="fields-container">
          <div ref="username" class="field-container">
            <span class="field-title">Account Name</span>
            <input class="field" placeholder="Some" spellcheck="false" autocomplete="off"/>
          </div>
          <div ref="password" class="field-container">
            <span class="field-title">Account Name</span>
            <input class="field" placeholder="Some" spellcheck="false" autocomplete="off"/>
          </div>
        </div>
        <div class="field-button-back" @click="back" v-show="showBackButton">
          Back
        </div>
        <div class="field-button" @click="next">
          Next
        </div>
      </div>
      <div class="text-center text-[18px] mx-auto hover:underline">Forgot your password?</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "EyeRoute",
  data() {
    return {
      fields: ['username', 'password'],
      showBackButton : false
    }
  },
  methods: {
    back() {
      this.showBackButton = false

      for (let field of this.fields) {
        this.$refs[field].style.transform = 'translateX(0)'
      }
    },
    next() {
      this.showBackButton = true

      for (let field of this.fields) {
        this.$refs[field].style.transform = 'translateX(-450px)'
      }
    }
  }
}
</script>

<style scoped>

.form {
  color: white;
  font-family: 'Hubballi', cursive;
  background: url("../static/kakashi.gif") center;
  @apply w-[450px] h-[600px] mx-auto mt-[50px] rounded-lg pt-[20px] overflow-hidden;
}

.form-header {
  width:  fit-content;
  @apply text-[24px] mx-auto block mb-[15px];
}

.field-container {
  transition: all .5s ease;
  @apply mx-auto;
}

.fields-container {
  @apply w-[900px] grid grid-cols-2;
}

.field-button {
  /*bg-[#0505dc]*/
  background : #5c5cef;
  @apply w-[80px] h-[30px] rounded-sm  text-center text-[19px] mt-2 float-right mr-[45px] cursor-pointer bg-[#5c5cef];
}

.field-button-back {
  @apply w-[80px] h-[30px] bg-transparent/10 rounded-sm backdrop-filter backdrop-blur-lg text-center text-[19px] float-left mt-2 ml-[45px] cursor-pointer;
}

.field-title {
  @apply block w-4/5 text-[18px];
}

.field {
  @apply bg-transparent/20 backdrop-filter backdrop-blur-lg h-[40px] w-[360px] mx-auto block outline-none pl-[20px] text-[20px] rounded-sm;
}

</style>
