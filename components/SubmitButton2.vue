<template>
  <div>
    <div class="submit-button" @click="submit" ref="root">
      <span>{{ buttonMessage }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubmitButton2.vue",
  data() {
    return {
      buttonMessage : 'Submit message'
    }
  },
  methods: {
    submit() {

    }
  }
}
</script>

<style scoped>

</style>
