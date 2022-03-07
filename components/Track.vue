<template>
  <div ref="root" class="bg-gradient-to-tl via-red-500 from-black to-black w-[370px] track">
    <div class="poster">
      <img src="../static/poster.jpg" alt=""/>
    </div>
    <div class="track-info">
      <span class="track-name">I`m Toxic</span><br>
      <span class="track-author">Khantrast</span>
    </div>
    <div class="control-panel">

    </div>
  </div>
</template>

<script>
export default {
  name: "Track"
}
</script>

<style scoped>

.track {
  @apply px-[15px] py-4
}

.poster {
  @apply w-[240px] h-[240px] mx-auto rounded-sm
}

.poster img {
  border: 1px solid;
  @apply rounded-md border-red-500
}

.track-info {
  font-family: "Hubballi", cursive;
  @apply mx-auto w-[240px] text-[#aed7cf] text-[17px]
}

.track-name {
}

.track-author {
  @apply font-bold relative bottom-[8px]
}

</style>
