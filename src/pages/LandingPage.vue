<template>
  <div class="landing-page q-pa-none">
    <LaunchAndScaling />
    <Features />
    <OurSuccess />
    <MeetOurTeam />
    <InnovativeTeam />
    <GetStarted />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import LaunchAndScaling from 'components/landing/LaunchAndScaling.vue';
import Features from 'components/landing/Features.vue';
import OurSuccess from 'components/landing/OurSuccess.vue';
import MeetOurTeam from 'components/landing/MeetOurTeam.vue';
import InnovativeTeam from 'components/landing/InnovativeTeam.vue';
import GetStarted from 'components/landing/GetStarted.vue';

export default defineComponent({
  name: 'LandingPage',
  components: {
    LaunchAndScaling,
    Features,
    OurSuccess,
    MeetOurTeam,
    InnovativeTeam,
    GetStarted,
  },
});
</script>

<style scoped>
.landing-page {
  min-height: 100vh; /* make full screen */
}
</style>
