<template>
  <div>
    <div class="choice-form" v-show="!logIn && !signUp">
      <div class="bg-transparent/20 backdrop-filter backdrop-blur-lg pb-3">
        <div class="form-header">Authorization</div>
        <div class="choice-button mb-1.5" @click="logIn = true">Log In</div>
        <div class="choice-button" @click="signUp = true">Sign Up</div>
      </div>
    </div>

    <LogInForm title="Log In" :fields="fieldsLog" v-show="logIn"/>
    <SignInForm v-show="signUp"/>
  </div>
</template>

<style scoped>

.choice-form {
  font-family: 'Hubballi', cursive;
  background : url("../static/choice.gif") center no-repeat;
  @apply rounded-md w-[350px] h-[350px] mx-auto mt-[50px] bg-[#089cf7] pb-3 pt-[200px];
}

.form-header {
  color : white;
  @apply text-[22px] mx-auto block w-full text-center
}

.choice-button {
  color : white;
  @apply bg-amber-500 mx-auto px-2 py-1 text-[18px] rounded-md cursor-pointer w-[80px] text-center;
}

</style>

<script>

export default {
  name: 'FormRoute',
  data() {
    return {
      logIn: false,
      signUp: false,
      fieldsLog: [
        {
          ref: 'username',
          fieldTitle: 'Account Name',
          placeHolder: 'SharapaGorg'
        },
        {
          ref: 'password',
          fieldTitle: 'Password',
          placeHolder: 'qwerty'
        }
      ]
    }
  }
}

</script>
