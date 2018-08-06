<template>
<div>
    <button @click="startVideo">Start Video</button>
    <video ref="video" width="640" height="480" autoplay></video>
</div>
</template>

<script>
export default {
  name: "Camera",
  methods: {
      startVideo() {
          let video = this.$refs.video;
          if(navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
            // Not adding `{ audio: true }` since we only want video now
            navigator.mediaDevices.getUserMedia({ video: true })
                .then(stream => {
                    video.src = window.URL.createObjectURL(stream);
                    video.play();

                });
            }
      }
  }
};
</script>

