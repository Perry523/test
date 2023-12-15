<template>
  <div>
    <button @click="notify">teste</button>
    <button @click="notify2">teste2</button>
  </div>
</template>
<script setup lang="ts">
navigator.serviceWorker.register("sw.js");

function notify() {
  Notification.requestPermission().then((result) => {
    if (result === "granted") {
      navigator.serviceWorker.ready.then((registration) => {
        // @ts-ignore
        registration.showNotification(Math.random(200), {
          body: "Buzz! Buzz!",
          icon: "../images/touch/chrome-touch-icon-192x192.png",
          vibrate: [200, 100, 200, 100, 200, 100, 200],
          tag: "vibration-sample",
        });
      });
    }
  });
}

function notify2() {
  Notification.requestPermission().then((result) => {
    if (result === "granted") {
      new Notification("teste", {
        body: "Buzz! Buzz 2!",
        icon: "../images/touch/chrome-touch-icon-192x192.png",
        vibrate: [200, 100, 200, 100, 200, 100, 200],
        tag: "vibration-sample",
      });
    }
  });
}
</script>
