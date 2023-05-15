<template>
  <div class="about">
    <iframe id='iframe' src="http://0.0.0.0:8001/" width="100%" height="800" style="border:none;"></iframe>
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
  setup() {
    onMounted(() => {
      console.log('onMounted')

      // In parent app
      // Just fire a message through iframe window
      const iframeWindow = document.getElementById("iframe").contentWindow;
      iframeWindow.postMessage("", "*");
      console.log('iframeWindow:', iframeWindow);

      // In parent app 
      // Bind a message event listener to window object
      window.addEventListener("message", function(event) {
        console.log('child calling the parent method');
      });
    })
  },
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
  }
}
</style>
