<template>
  <section class="success-stories">
    <!-- Full background map -->
    <q-img :src="frame2" class="background-map" spinner-color="white" cover />

    <!-- Overlay content -->
    <div class="overlay q-pa-xl column items-center justify-center text-center">
      <h2 class="success-title q-mb-sm">Your Success is Our Success</h2>
      <p class="success-subtitle q-mb-xl">Success stories & Case studies</p>

      <!-- Story container -->
      <div
        class="story-container flex row items-center justify-between q-pa-md"
        style="position: relative; flex-wrap: nowrap"
      >
        <!-- Left arrow -->
        <q-btn
          flat
          round
          icon="arrow_back_ios"
          size="lg"
          color="white"
          class="arrow-btn left-arrow"
          @click="prevStory"
          style="left: -10%"
        />

        <!-- Middle content wrapper -->
        <div
          class="flex row items-center justify-center q-gutter-md"
          style="flex: 1; position: relative; flex-wrap: nowrap"
        >
          <!-- Transparent card -->
          <q-card flat bordered class="transparent-card"></q-card>

          <!-- Testimonial card -->
          <q-card
            flat
            class="testimonial-card q-pa-lg text-white"
            style="position: relative; z-index: 2; flex-shrink: 0"
          >
            <div class="row q-mb-md bordered-pill align-left">
              <q-img :src="currentStory.logo" style="width: 100px; height: 40px" />
              <span>|</span>
              <span class="q-ml-sm text-grey-3">{{ currentStory.url }}</span>
            </div>
            <div class="row">
              <q-img
                src="~assets/icons/story_quote.png"
                alt="Quote Icon"
                class="text-white align-left"
                style="
                  width: 50px;
                  height: 50px;
                  float: left;
                  margin-bottom: 20px;
                  margin-top: 20px;
                "
              />
            </div>
            <p class="text-body2 text-left">{{ currentStory.text }}</p>
            <q-btn
              flat
              label="Read the story"
              icon-right="arrow_forward"
              class="q-mt-md read-more-btn"
            />
          </q-card>

          <!-- Project screenshot card -->
          <q-card flat bordered class="project-card q-pa-md" style="flex-grow: 1">
            <q-img :src="currentStory.image" class="rounded-borders" />
          </q-card>
        </div>

        <!-- Right arrow -->
        <q-btn
          flat
          round
          icon="arrow_forward_ios"
          size="lg"
          color="white"
          class="arrow-btn right-arrow"
          @click="nextStory"
          style="right: -10%"
        />
      </div>
    </div>

    <!-- Navigation lines always on background -->
    <div class="navigation-lines">
      <div
        v-for="(story, index) in stories"
        :key="index"
        class="nav-line"
        :class="{ active: index === currentIndex }"
        @click="goToStory(index)"
      ></div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import tryDiscsLogo from '../../assets/tryDiscs_logo.png';
import ssInOurSuccess from '../../assets/ss_in_ourSuccess.png';
import frame2 from '../../assets/frames/frame2.png';
import dummy1 from '../../assets/gall_logo.png';
import dummy2 from '../../assets/papello_logo.png';
import dummy3 from '../../assets/quasar-logo-vertical.svg';

interface Story {
  logo: string;
  url: string;
  text: string;
  image: string;
}

export default defineComponent({
  name: 'OurSuccess',
  setup() {
    const stories = ref<Story[]>([
      {
        logo: tryDiscsLogo,
        url: 'https://trydiscs.com/',
        text: 'Working with LONGWApps has been a great experience. Their team is responsive, skilled, and delivered exactly what we needed on time. The software runs smoothly, and their support has been excellent throughout. Highly recommended!',
        image: ssInOurSuccess,
      },
      {
        logo: tryDiscsLogo,
        url: 'https://anotherstory.com/',
        text: 'Another client success story goes here. Example testimonial content.',
        image: dummy1,
      },
      {
        logo: tryDiscsLogo,
        url: 'https://thirdstory.com/',
        text: 'This is a third story with dummy image and testimonial content.',
        image: dummy2,
      },
      {
        logo: tryDiscsLogo,
        url: 'https://fourthstory.com/',
        text: 'Fourth story example to demonstrate navigation using arrows.',
        image: dummy3,
      },
    ]);

    const currentIndex = ref(0);
    const currentStory = computed(() => stories.value[currentIndex.value]!);

    const prevStory = () => {
      currentIndex.value = (currentIndex.value - 1 + stories.value.length) % stories.value.length;
    };

    const nextStory = () => {
      currentIndex.value = (currentIndex.value + 1) % stories.value.length;
    };

    const goToStory = (index: number) => {
      currentIndex.value = index;
    };

    return {
      stories,
      frame2,
      currentIndex,
      currentStory,
      prevStory,
      nextStory,
      goToStory,
    };
  },
});
</script>

<style scoped>
.success-stories {
  margin-top: -66px;
  min-height: 100vh;
  position: relative;
  width: 100%;
  overflow: hidden;
}

.success-title {
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-family: 'Titles/Title/Family', sans-serif;
  font-weight: 100;
  font-size: clamp(36px, 5vw, 57.6px);
  line-height: 1;
  text-align: center;
}

.success-subtitle {
  font-family: 'Headings/Normal/Family', sans-serif;
  font-weight: 10;
  font-size: clamp(20px, 3vw, 28px);
  line-height: 1.2;
  text-align: center;
  color: #bababa;
  padding: 4px 8px;
}

.background-map {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}

.overlay {
  position: relative;
  z-index: 2;
  width: 100%;
  min-height: 100vh;
  padding: clamp(16px, 5vw, 40px);
}

.project-card {
  border-radius: 30px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  height: auto;
  max-height: 400px;
  margin-top: 10%;
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: clamp(300px, 60vw, 700px);
}

.project-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.story-container {
  position: relative;
  margin-top: 50px;
  width: 100%;
  max-width: 1200px;
  flex-wrap: wrap;
}

.arrow-btn {
  z-index: 5 !important;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.left-arrow {
  left: clamp(-40px, -5vw, -10px);
}

.right-arrow {
  right: clamp(-40px, -5vw, -10px);
}

.transparent-card {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 30px;
  height: clamp(300px, 50vw, 550px);
  position: absolute;
  left: clamp(-40px, -5vw, -80px);
  width: clamp(300px, 80vw, 1000px);
  z-index: 1;
  top: 0;
}

.testimonial-card {
  background: transparent;
  min-height: 300px;
  color: white;
  width: 100%;
  max-width: clamp(300px, 40vw, 400px);
}

.bordered-pill {
  border: 2px solid white !important;
  border-radius: 999px !important;
  padding: 5px 15px;
  display: flex;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.3);
  height: 50px;
  width: fit-content;
  gap: 15px;
  box-sizing: border-box;
  z-index: 3;
  padding-right: 50px;
}

.bordered-pill q-img {
  height: 40px;
  width: auto;
}

.align-left {
  justify-content: flex-start;
  width: fit-content;
}

.text-body2 {
  font-family: 'Body/Base/Family', sans-serif;
  font-weight: normal;
  font-style: normal;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0%;
}

.read-more-btn {
  border: 2px solid #a3a3a3;
  border-radius: 7px;
  padding: 5px 15px;
  display: flex;
  align-items: center;
  background-color: #a3a3a3;
  text-transform: none;
}

/* Navigation lines fixed on background image */
.navigation-lines {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  justify-content: center;
  align-items: center;
  z-index: 10;
}

.nav-line {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: #c2005e;
  cursor: pointer;
  transition: all 0.3s ease;
}

.nav-line.active {
  width: 30px;
  height: 7px;
  border-radius: 5px;
  background-color: #c2005e;
  opacity: 1;
}

@media (max-width: 768px) {
  .story-container {
    flex-direction: column;
    align-items: center;
    gap: 20px;
  }

  .transparent-card {
    display: none;
  }

  .testimonial-card {
    max-width: 100%;
    margin-bottom: 20px;
  }

  .project-card {
    max-width: 100%;
    margin-top: 0;
  }

  .success-title {
    font-size: clamp(28px, 8vw, 40px);
  }

  .success-subtitle {
    font-size: clamp(16px, 5vw, 22px);
  }
}

@media (max-width: 480px) {
  .overlay {
    padding: 16px;
  }

  .testimonial-card {
    padding: 16px;
  }

  .project-card {
    max-height: 300px;
  }
  .left-arrow {
    left: 0;
    top: 40%;
  }

  .right-arrow {
    right: 0;
    top: 40%;
  }

  .arrow-btn {
    size: 35px;
  }
}
</style>
