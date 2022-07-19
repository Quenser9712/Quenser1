<template>
  <div>
    <div class="watch">
      <div class="time">00:00:00</div>
      <div class="btn">
        <button id="start" @click="time()">start</button>
        <button id="stop" @click="stop()">stop</button>
        <button id="reset" @click="reset()">reset</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  mounted() {},
  
  methods: {
    time() {
      const time = document.querySelector('.time')
      let sss = 0
      let mmm = 59
      let hhh = 23

     setInterval(() => {
        sss++
        if (sss == 60) {
          mmm++
          if (mmm == 60) {
            hhh++
            hhh = hhh % 24
          }
          mmm = mmm % 60
        }
        sss = sss % 60
        time.innerText = hhh + ':' + mmm + ':' + sss
      }, 1000)
   
    },
    reset() {
      const time = document.querySelector('.time')
      time.innerText = '00:00:00'
    },
  },
}
</script>
<style scoped></style>
