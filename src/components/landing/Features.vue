<template>
  <section class="features q-pa-xl bg-grey-2">
    <!-- Title & Subtitle -->
    <div class="text-center" style="padding-bottom: 40px">
      <div class="text-center q-mb-md">
        <!-- change q-mb-xl to q-mb-md -->
        <h2 class="section-title" style="margin-bottom: 8px">
          Powerful Features for Modern Development
        </h2>
        <p class="text-subtitle2 text-grey-7" style="margin-top: 0">
          We provide everything you need to build, deploy, and scale your applications.
        </p>
      </div>
    </div>

    <!-- Features Grid -->
    <div class="row q-col-gutter-xl justify-center">
      <div v-for="(feature, index) in features" :key="index" class="col-12 col-md-4">
        <q-card flat bordered class="q-pa-lg text-left shadow-1">
          <!-- Icon with background -->
          <div class="q-mb-md flex items-center">
            <div class="icon-wrapper flex items-center justify-center">
              <q-img
                :src="feature.icon"
                alt="feature icon"
                width="28px"
                height="28px"
                fit="contain"
              />
            </div>
          </div>

          <!-- Title & Description -->
          <h6 class="text-h6 text-weight-bold q-mb-sm">{{ feature.title }}</h6>
          <p class="text-body2 text-grey-7">{{ feature.description }}</p>
        </q-card>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

// Import all icons directly
import productEnIcon from 'src/assets/icons/product_en.png';
import aiIcon from 'src/assets/icons/AI.png';
import systemInteIcon from 'src/assets/icons/system_inte.png';
import webDevIcon from 'src/assets/icons/web_dev.png';
import mobileDevIcon from 'src/assets/icons/mobile_dev.png';
import uiuxIcon from 'src/assets/icons/ui_ux.png';

export default defineComponent({
  name: 'FeaturesSection',
  setup() {
    const features = [
      {
        title: 'Product Engineering',
        description:
          "With mobile usage dominating digital space, we craft powerful, intuitive apps that put your business in your users' pockets — anytime, anywhere.",
        icon: productEnIcon,
      },
      {
        title: 'AI Automation',
        description:
          "With mobile usage dominating digital space, we craft powerful, intuitive apps that put your business in your users' pockets — anytime, anywhere.",
        icon: aiIcon,
      },
      {
        title: 'System Integration',
        description:
          'We connect the dots between your systems, creating a unified digital ecosystem that enhances efficiency, data flow, and business intelligence.',
        icon: systemInteIcon,
      },
      {
        title: 'Web Development',
        description:
          'Empowering brands to go digital with high-performance, responsive websites built for scalability and user engagement in the modern web era.',
        icon: webDevIcon,
      },
      {
        title: 'Mobile App Development',
        description:
          "With mobile usage dominating digital space, we craft powerful, intuitive apps that put your business in your users' pockets — anytime, anywhere.",
        icon: mobileDevIcon,
      },
      {
        title: 'UI/UX Design',
        description:
          'We design experiences that feel natural, intuitive, and human — because great design isn’t about features, it’s about how users feel.',
        icon: uiuxIcon,
      },
    ];

    return { features };
  },
});
</script>

<style scoped>
.features {
  min-height: 600px;
}

.q-card {
  border-radius: 12px;
  height: 100%;
}

.icon-wrapper {
  width: 56px;
  height: 56px;
  border-radius: 12px;
  background-color: #f2effb;
}

.section-title {
  font-size: 28px;
  font-weight: bold;
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text; /* standard property for compatibility */
  -webkit-background-clip: text; /* Safari/Chrome */
  -webkit-text-fill-color: transparent;
  color: transparent;
}
</style>
