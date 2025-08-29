<template>
  <section class="launch-scaling q-pa-lg flex flex-center">
    <div class="relative-container">
      <!-- Grey rotated rectangle -->
      <div class="rotated-bg"></div>

      <!-- Main image -->
      <q-img src="~/assets/our_team.png" alt="Our Team" class="team-image">
        <!-- Overlay wrapper -->
        <div class="overlay-text">
          <!-- Background layer -->
          <div class="overlay-text-layer"></div>
          <!-- Text layer -->
          <span class="overlay-text-span">Meet Our Team → </span>
        </div>
      </q-img>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'LaunchAndScaling',
});
</script>

<style scoped>
.launch-scaling {
  min-height: 100vh; /* full window height */
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden; /* prevent rectangle leaking outside */
  position: relative;
}

/* Container for layering */
.relative-container {
  position: relative;
  display: inline-block;
  z-index: 2;
}

/* Grey rectangle background rotated */
.rotated-bg {
  position: absolute;
  top: 10px;
  left: 2px;
  width: 100%;
  height: 100%;
  background: #bababa; /* light grey */
  transform: rotate(5deg);
  z-index: 1;
}

/* Main image styling */
.team-image {
  position: relative;
  display: block;
  z-index: 2;
  width: 900px; /* adjust as per your layout */
  max-width: 90vw; /* responsive */
  height: auto;
  overflow: hidden;
}

/* Overlay wrapper */
.overlay-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%; /* match image width */
  text-align: center;
  z-index: 3;
}

/* Background layer behind text */
.overlay-text-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%; /* match image width */
  height: 100%; /* full height of text container */
  background: rgba(255, 255, 255, 0.6);
  z-index: -1; /* behind the text */
}

/* Text with gradient */
.overlay-text-span {
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 600;
  font-size: 1.2rem;
  white-space: nowrap;
  position: relative;
  z-index: 2;
}
</style>
