<template>
  <section class="launch-scaling">
    <!-- Background frame image -->
    <q-img
      :src="frameImage"
      alt="Frame Background"
      class="background-img"
      spinner-color="white"
      :ratio="16 / 9"
    />

    <!-- Overlay content -->
    <div class="overlay">
      <div class="main-heading">Engineering Your Next Digital Project</div>

      <!-- Description -->
      <p class="description">
        From strategy to delivery, we build and scale projects with precision.
      </p>
      <div class="btn-set flex gap-5">
        <q-btn unelevated rounded class="custom-btn">
          <div style="display: flex; align-items: center">
            <span>Start Your Project</span>
            <img :src="rocketIcon" alt="rocket" />
          </div>
        </q-btn>
        <q-btn unelevated rounded class="custom-btn">
          <div style="display: flex; align-items: center">
            <span>Explore Services</span>
            <img :src="searchIcon" alt="search" />
          </div>
        </q-btn>
      </div>
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
import frameImage from 'src/assets/frames/frame1_1.png';
import rocketIcon from 'src/assets/icons/rocket_icon.svg';
import searchIcon from 'src/assets/icons/search_icon.svg';
import uniworLogo from 'src/assets/uniwor_logo.png';
import tryDiscsLogo from 'src/assets/tryDiscs_logo.png';
import papelloLogo from 'src/assets/papello_logo.png';
import xvantageLogo from 'src/assets/xvantage_logo.png';
import gallLogo from 'src/assets/gall_logo.png';

export default defineComponent({
  name: 'LaunchAndScaling',
  setup() {
    const frameImageRef = ref(frameImage);
    return {
      frameImage: frameImageRef,
      searchIcon,
      rocketIcon,
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
  overflow-x: hidden; /* Prevent horizontal scrollbar */
}

.background-img {
  margin-top: -66px;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%; /* Ensure image fits viewport width */
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.main-heading {
  margin: 0;
  line-height: 1.2;
  position: relative;
  font-size: 40px;
  font-weight: 800;
  color: #fff;
  text-align: center;
  text-shadow: 2px 4px 15px rgba(0, 0, 0, 0.5);
  white-space: nowrap; /* Keep heading on one line for larger screens */
  max-width: 90%; /* Prevent overflow */
}

.description {
  font-size: 1.25rem;
  color: #f2effb;
  margin-bottom: 40px;
  margin-top: 25px;
  font-weight: 800;
  text-align: center;
  position: relative;
  line-height: 1.5;
  max-width: 90%; /* Prevent overflow */
}

.overlay {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5vw; /* Responsive padding */
  text-align: center;
  max-width: 800px;
  width: 100%;
}

.btn-set {
  display: flex;
  gap: 20px;
  flex-wrap: wrap; /* Allow buttons to wrap on smaller screens */
  justify-content: center;
}

.btn-set span {
  color: #000000;
  white-space: nowrap;
}

.btn-set img {
  width: 20px;
  height: 20px;
  margin-left: 8px;
}

.custom-btn {
  font-family: 'Inter', sans-serif;
  font-weight: 800;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0%;
  color: #5b32a1;
  width: 220px;
  height: 54px;
  padding: 15px 25px;
  border-radius: 50px;
  background-color: #f2effb;
  text-transform: none;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
  transition: all 0.3s ease;
  position: relative;
}

.custom-btn:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.bottom-layer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #ffffff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 5vw; /* Responsive padding */
  z-index: 1;
  flex-wrap: wrap; /* Allow logos to wrap on smaller screens */
  gap: 10px; /* Add spacing between logos */
}

.bottom-layer img {
  max-width: 100px; /* Limit logo size for responsiveness */
  height: auto;
  object-fit: contain;
}

/* Media Queries for Responsiveness */
@media (max-width: 768px) {
  .main-heading {
    font-size: 2rem; /* Smaller font size on mobile */
    line-height: 1.3;
    white-space: normal; /* Allow wrapping on mobile */
  }

  .description {
    font-size: 1rem;
    line-height: 1.4;
    margin-bottom: 20px;
  }

  .overlay {
    padding: 3vw;
  }

  .custom-btn {
    width: 180px; /* Smaller buttons on mobile */
    font-size: 14px;
    padding: 10px 20px;
  }

  .bottom-layer {
    padding: 10px 3vw;
    justify-content: center; /* Center logos on mobile */
  }

  .bottom-layer img {
    max-width: 80px; /* Smaller logos on mobile */
  }
}

@media (max-width: 480px) {
  .main-heading {
    font-size: 1.5rem;
  }

  .description {
    font-size: 0.9rem;
  }

  .custom-btn {
    width: 160px;
    font-size: 12px;
  }
}
</style>
