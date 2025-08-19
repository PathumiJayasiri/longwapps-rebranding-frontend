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
    <div class="overlay">
      <q-btn unelevated rounded class="custom-btn">
        <!-- Star image inside button -->
        <div style="display: flex; align-items: center">
          <img :src="starImage" alt="star" style="width: 20px; height: 20px; margin-right: 8px" />
          <span>Build with AI</span>
        </div>
      </q-btn>

      <h1 class="main-heading"><span class="highlight">Launch & Scale</span> with Us</h1>

      <!-- Description -->
      <p class="description">
        We craft scalable, secure, and user-centric software that accelerates your business growth
        and digital transformation.
      </p>
      <q-btn unelevated color="" class="hire-btn" label="Hire a Product Engineering Team" />
    </div>
    <div class="bottom-layer">
      <img :src="uniworLogo" alt="Uniwor Logo" />
      <img :src="tryDiscsLogo" alt="TryDiscs Logo" />
      <img :src="papelloLogo" alt="Papello Logo" />
      <img :src="xvantageLogo" alt="XVantage Logo" />
      <img :src="gallLogo" alt="Gall Logo" />
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import frameImage from 'src/assets/frames/frame1.png';
import starIcon from 'src/assets/star_icon.png';
import uniworLogo from 'src/assets/uniwor_logo.png';
import tryDiscsLogo from 'src/assets/tryDiscs_logo.png';
import papelloLogo from 'src/assets/papello_logo.png';
import xvantageLogo from 'src/assets/xvantage_logo.png';
import gallLogo from 'src/assets/gall_logo.png';

export default defineComponent({
  name: 'LaunchAndScaling',
  setup() {
    const frameImageRef = ref(frameImage);
    const starImage = ref(starIcon); // only one reference needed
    return {
      frameImage: frameImageRef,
      starImage,
      uniworLogo,
      tryDiscsLogo,
      papelloLogo,
      xvantageLogo,
      gallLogo,
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
.main-heading {
  font-size: 3rem;
  font-weight: bold;
  margin: 0;
  line-height: 1.2;
}

.main-heading .highlight {
  color: #ff0080;
}

.description {
  font-size: 1.125rem;
  color: #555;
  max-width: 700px;
  margin-bottom: 40px;
  margin-top: 25px;
}
.overlay {
  display: flex;
  flex-direction: column; /* stack children vertically */
  align-items: center; /* center horizontally */
  padding: 80px;
  text-align: center;
  max-width: 800px;
  width: 100%;
}

.custom-btn {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0%;
  color: #5b32a1; /* text color */
  width: 180px;
  height: 54px;
  padding: 15px 25px;
  border-radius: 50px;
  background-color: transparent; /* make inside transparent */
  border: 2px solid #ffffff; /* white border */
  box-shadow: 0 4px 10px rgba(231, 224, 224, 0.3); /* white shadow */
  text-transform: none;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
  transition: all 0.3s ease; /* smooth hover effect */
}

.custom-btn:hover {
  background-color: rgba(255, 255, 255, 0.1); /* slight hover effect */
}
.hire-btn {
  font-family: Arial, Helvetica, sans-serif;
  width: 312px;
  height: 54px;
  padding: 15px 20px;
  gap: 5px;
  border-radius: 10px;
  background-color: #7745cd;
  opacity: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
.bottom-layer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #ffffff; /* White background */
  display: flex;
  justify-content: space-between; /* Space between images */
  align-items: center; /* Vertical alignment */
  padding: 20px 40px; /* Padding for spacing */
  z-index: 1; /* Ensure it’s above the background image */
}
.bottom-layer img {
  width: 80px; /* adjust size as needed */
  height: auto;
}
</style>
