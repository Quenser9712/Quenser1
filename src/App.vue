<template>
  <div class="body">
    <h1>APP</h1>
    <test
      :timer="formattedTime"
      :state="timerState"
      @start="start"
      @pause="pause"
      @stop="stop"
    />
  </div>
</template>

<script>
import test from './components/test.vue'

export default {
  components: {
    test,
  },
  data() {
    return {
      timerState: 'stopped',
      currentTimer: 0,
      formattedTime: '00:00:00',
      ticker: undefined,
      snackbar: false,
    }
  },
  methods: {
    start() {
      if (this.timerState !== 'running') {
        this.tick()
        this.timerState = 'running'
      }
    },
    pause() {
      window.clearInterval(this.ticker)
      this.timerState = 'paused'
    },
    stop() {
      window.clearInterval(this.ticker)
      this.currentTimer = 0
      this.formattedTime = '00:00:00'
      this.timerState = 'stopped'
    },
    tick() {
      this.ticker = setInterval(() => {
        this.currentTimer++
        this.formattedTime = this.formatTime(this.currentTimer)
      }, 250)
    },
    formatTime(seconds) {
      let measuredTime = new Date(null)
      measuredTime.setSeconds(seconds)
      let MHSTime = measuredTime.toISOString().substr(11, 8)
      return MHSTime
    },
  },
}
</script>

<style></style>
