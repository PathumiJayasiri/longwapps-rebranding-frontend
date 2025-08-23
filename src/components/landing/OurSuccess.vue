<template>
  <section class="success-stories q-pa-xl">
    <!-- Background map -->
    <q-img :src="frame2" class="background-map" spinner-color="white" :ratio="16 / 9" />

    <!-- Overlay content -->
    <div class="overlay q-pa-xl column items-center justify-center text-center">
      <h2 class="success-title q-mb-sm">Your Success is Our Success</h2>
      <p class="success-subtitle q-mb-xl">Success stories & Case studies</p>

      <!-- Slider -->
      <q-carousel
        v-model="slide"
        animated
        swipeable
        arrows
        infinite
        navigation
        class="w-full max-w-5xl"
      >
        <q-carousel-slide
          v-for="(story, index) in stories"
          :key="index"
          :name="index"
          class="row items-center justify-between q-pa-md"
        >
          <!-- Testimonial card -->
          <q-card
            flat
            bordered
            class="testimonial-card q-pa-lg col-12 col-md-5 bg-grey-8 text-white"
          >
            <div class="row items-center q-mb-md">
              <q-img :src="story.logo" style="width: 40px; height: 40px" />
              <span class="q-ml-sm text-grey-3">{{ story.url }}</span>
            </div>
            <q-icon name="format_quote" size="40px" class="q-mb-md text-pink-6" />
            <p class="text-body2">{{ story.text }}</p>
            <q-btn flat round label="Read the story ➔" color="grey-4" class="q-mt-md" />
          </q-card>

          <!-- Project screenshot card -->
          <q-card flat bordered class="project-card col-12 col-md-6 q-pa-md">
            <q-img :src="story.image" class="rounded-borders" />
          </q-card>
        </q-carousel-slide>
      </q-carousel>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import tryDiscsLogo from '../../assets/tryDiscs_logo.png';
import ssInOurSuccess from '../../assets/ss_in_ourSuccess.png';
import frame2 from '../../assets/frames/frame2.png';

export default defineComponent({
  name: 'SuccessStories',
  setup() {
    const slide = ref(0);
    const stories = ref([
      {
        logo: tryDiscsLogo,
        url: 'https://trydiscs.com/',
        text: `Working with LONGWApps has been a great experience. Their team is responsive, skilled, and delivered exactly what we needed on time. The software runs smoothly, and their support has been excellent throughout. Highly recommended!`,
        image: ssInOurSuccess,
      },
    ]);
    return { slide, stories, frame2 };
  },
});
</script>

<style scoped>
.success-stories {
  position: relative;
  /* min-height: 500px; */
  background-color: #0b0c2a;
  background-image: url('src/assets/frames/frame2.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.success-title {
  /* Gradient text */
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text; /* standard property for compatibility */
  -webkit-background-clip: text; /* Safari/Chrome */
  -webkit-text-fill-color: transparent;
  color: transparent;

  font-family: 'Titles/Title/Family', sans-serif; /* replace with actual font if needed */
  font-weight: 100; /* ExtraBold */
  font-style: normal; /* ExtraBold usually mapped as font-weight, keep style normal */
  font-size: 57.6px; /* Titles/Title/Size */
  line-height: 57.6px;
  letter-spacing: 0;
  text-align: center;
}
.success-subtitle {
  font-family: 'Headings/Normal/Family', sans-serif; /* replace with actual font */
  font-weight: 10; /* Medium */
  font-size: 28px; /* Headings/Normal/Size */
  line-height: 28.8px;
  letter-spacing: 0;
  text-align: center;
  padding: 4px 8px;
  color: #bababa;
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

.testimonial-card {
  min-height: 300px;
}

.project-card img {
  width: 100%;
  height: auto;
}

.q-carousel .q-carousel__navigation {
  bottom: -30px;
}
</style>
