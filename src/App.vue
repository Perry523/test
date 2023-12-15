<template>
  <div>
    <button @click="notify">teste</button>
  </div>
</template>
<script setup lang="ts">
function notify() {
  Notification.requestPermission().then((permission) => {
    if (permission === 'granted') {
      setTimeout(() => {
        new Notification('Hello, world!')
      }, 5000)
    }
  })
}
</script>
