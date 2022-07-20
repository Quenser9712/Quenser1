<template>
  <div>
    <div class="watch">
      <div>
        {{ timer }}
      </div>
      <button @click="$emit('start')" :disabled="state == 'running'">
        Start
      </button>
      <button
        @click="$emit('pause')"
        :disabled="state == 'stopped' || state == 'paused'"
      >
        Pause
      </button>
      <button @click="$emit('stop')" :disabled="state == 'stopped'">
        Stop
      </button>
    </div>
  </div>
</template> 

<script>
export default {
  name: 'Timer',
  props: ['timer', 'state'],
}
</script>
<style scoped></style>
