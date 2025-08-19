<template>
  <section class="launch-scaling">
    <!-- Background frame image-->
    <q-img
      :src="frameImage"
      alt="Frame Background"
      class="background-img"
      spinner-color="white"
      :ratio="16 / 9"
    />

    <!-- Overlay content -->
    <div class="overlay text-center">
      <h2 class="text-h3">Launch & Scaling</h2>
      <p class="text-subtitle2 q-mt-md">Describe how your product launches and scales here.</p>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import frameImage from 'src/assets/frames/frame1.png';

export default defineComponent({
  name: 'LaunchAndScaling',
  setup() {
    const frameImageRef = ref(frameImage);
    return {
      frameImage: frameImageRef,
    };
  },
});
</script>

<style scoped>
.launch-scaling {
  margin-top: -66px;
  position: relative;
  min-height: 100vh;
  padding-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background-image: url('src/assets/frames/frame1.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.background-img {
  margin-top: -66px;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.overlay {
  padding: 80px;
  text-align: center;
  max-width: 800px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;
}
</style>
