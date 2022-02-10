<template>
    <div class="text-center">
      <div>
        KPD
      </div>
      <v-progress-circular
        :rotate="-90"
        :size="100"
        :width="15"
        :value="value"
        color="primary"
      >
        {{ value }} %
      </v-progress-circular>

    </div>
</template>

<script>
export default {
  name: "Progress",
  data () {
    return {
      interval: {},
      value: 0,
    }
  },
  beforeDestroy () {
    clearInterval(this.interval)
  },
  mounted () {
    this.interval = setInterval(() => {
      if (this.value === 100) {
        return (this.value = 0)
      }
      this.value += 10
    }, 5000)
  },
}
</script>

<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>
