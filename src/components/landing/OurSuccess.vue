<template>
  <section class="success-stories q-pa-xl">
    <!-- Background map -->
    <q-img :src="frame2" class="background-map" spinner-color="white" :ratio="16 / 9" />

    <!-- Overlay content -->
    <div class="overlay q-pa-xl column items-center justify-center text-center">
      <h2 class="success-title q-mb-sm">Your Success is Our Success</h2>
      <p class="success-subtitle q-mb-xl">Success stories & Case studies</p>

      <!-- Story container -->
      <div
        class="story-container row items-center justify-between q-pa-md"
        style="position: relative"
      >
        <!-- Left arrow -->
        <q-btn
          flat
          round
          icon="arrow_back_ios"
          size="lg"
          color="white"
          class="q-mr-md arrow-btn"
          @click="prevStory"
        />

        <!-- Transparent card (behind testimonial) -->
        <q-card
          flat
          bordered
          class="transparent-card"
          style="position: absolute; left: 0; width: 60%; height: 100%; z-index: 1; top: 0"
        ></q-card>

        <!-- Testimonial card -->
        <q-card
          flat
          bordered
          class="testimonial-card q-pa-lg col-12 col-md-5 text-white"
          style="position: relative; z-index: 2"
        >
          <div class="row items-center q-mb-md">
            <q-img :src="currentStory.logo" style="width: 40px; height: 40px" />
            <span class="q-ml-sm text-grey-3">{{ currentStory.url }}</span>
          </div>
          <q-icon name="format_quote" size="40px" class="q-mb-md text-pink-6" />
          <p class="text-body2">{{ currentStory.text }}</p>
          <q-btn flat round label="Read more" color="grey-4" class="q-mt-md" />
        </q-card>

        <!-- Project screenshot card -->
        <q-card
          flat
          bordered
          class="project-card col-12 col-md-6 q-pa-md"
          style="position: relative; z-index: 1; margin-left: -50px"
        >
          <q-img :src="currentStory.image" class="rounded-borders" />
          <div class="row q-mt-sm q-gutter-sm">
            <q-btn flat round icon="star" size="sm" color="yellow" />
            <q-btn flat round icon="flight_takeoff" size="sm" color="blue" />
            <q-btn flat round icon="warning" size="sm" color="red" />
            <q-btn flat round icon="compare_arrows" size="sm" color="green" />
          </div>
        </q-card>

        <!-- Right arrow -->
        <q-btn
          flat
          round
          icon="arrow_forward_ios"
          size="lg"
          color="white"
          class="q-ml-md arrow-btn"
          @click="nextStory"
        />
      </div>

      <!-- Navigation dots -->
      <div class="navigation-dots q-mt-md">
        <q-icon
          v-for="(story, index) in stories"
          :key="index"
          name="lens"
          size="10px"
          :color="index === currentIndex ? 'white' : 'grey-4'"
          :style="{ opacity: index === currentIndex ? 1 : 0.3, cursor: 'pointer' }"
          @click="goToStory(index)"
        />
      </div>
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
        text: 'Working with LONGWApps has been a great experience. Highly recommended!',
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
  position: relative;
  background-color: #0b0c2a;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.success-title {
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-family: 'Titles/Title/Family', sans-serif;
  font-weight: 100;
  font-size: 57.6px;
  line-height: 57.6px;
  text-align: center;
}
.success-subtitle {
  font-family: 'Headings/Normal/Family', sans-serif;
  font-weight: 10;
  font-size: 28px;
  line-height: 28.8px;
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
  opacity: 0.2;
  object-fit: cover;
  z-index: 1;
}

.overlay {
  position: relative;
  z-index: 2;
}

.project-card {
  border-radius: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.project-card img {
  width: 100%;
  height: auto;
}

.story-container {
  position: relative;
}

/* Make arrows above other cards */
.arrow-btn {
  z-index: 5 !important;
}

.navigation-dots {
  display: flex;
  gap: 8px;
  justify-content: center;
}

.transparent-card {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  height: 500px;
}

.testimonial-card {
  background: transparent;
  min-height: 300px;
  border-radius: 15px;
  color: white;
  box-shadow: none;
}
</style>
