<template>
  <section class="testimonials q-pa-xl" style="width: 100vw">
    <!-- Heading -->
    <div class="text-center q-mb-xl">
      <h2 class="text-h5 text-primary text-bold main-title">Trusted by Innovative Teams</h2>
      <p class="text-subtitle2 q-mt-sm">
        See what our customers say about their experience using our platform.
      </p>
    </div>

    <!-- Testimonials Row -->
    <div class="row q-col-gutter-lg justify-between justify-center">
      <!-- Card 1 -->
      <q-card class="testimonial-card col-12 col-md-3">
        <q-card-section>
          <div class="q-mb-sm">
            <q-icon v-for="n in 5" :key="n" name="star" color="amber" size="20px" />
          </div>
          <p class="testimonial-text">
            "Implementing this platform has reduced our deployment time by 70% and significantly
            improved our team's productivity."
          </p>
        </q-card-section>

        <q-separator />

        <q-card-section class="row items-center no-wrap q-mt-sm">
          <q-avatar size="40px">
            <img src="https://randomuser.me/api/portraits/women/44.jpg" />
          </q-avatar>
          <div class="q-ml-md">
            <div class="text-subtitle2 text-bold">Sarah Johnson</div>
            <div class="text-caption text-grey">CTO, TechCorp</div>
          </div>
        </q-card-section>
      </q-card>

      <!-- Card 2 -->
      <q-card class="testimonial-card col-12 col-md-3">
        <q-card-section>
          <div class="q-mb-sm">
            <q-icon v-for="n in 5" :key="n" name="star" color="amber" size="20px" />
          </div>
          <p class="testimonial-text">
            "The integration capabilities are remarkable. We connected our entire tech stack within
            days, not weeks as we expected."
          </p>
        </q-card-section>

        <q-separator />

        <q-card-section class="row items-center no-wrap q-mt-sm">
          <q-avatar size="40px">
            <img src="https://randomuser.me/api/portraits/men/46.jpg" />
          </q-avatar>
          <div class="q-ml-md">
            <div class="text-subtitle2 text-bold">Michael Chen</div>
            <div class="text-caption text-grey">Lead Developer, StartupX</div>
          </div>
        </q-card-section>
      </q-card>

      <!-- Card 3 -->
      <q-card class="testimonial-card col-12 col-md-3">
        <q-card-section>
          <div class="q-mb-sm">
            <q-icon v-for="n in 4" :key="n" name="star" color="amber" size="20px" />
            <q-icon name="star_border" color="amber" size="20px" />
          </div>
          <p class="testimonial-text">
            "The analytics and monitoring features have given us unprecedented visibility into our
            application performance."
          </p>
        </q-card-section>

        <q-separator />

        <q-card-section class="row items-center no-wrap q-mt-sm">
          <q-avatar size="40px">
            <img src="https://randomuser.me/api/portraits/women/47.jpg" />
          </q-avatar>
          <div class="q-ml-md">
            <div class="text-subtitle2 text-bold">Emily Rodriguez</div>
            <div class="text-caption text-grey">Product Manager, EnterpriseY</div>
          </div>
        </q-card-section>
      </q-card>
    </div>

    <!-- Link -->
    <div class="text-right q-mt-lg">
      <a href="#" class="view-link">View All Customer Stories</a>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TestimonialsSection',
});
</script>

<style scoped>
.testimonials {
  background-color: #f2eafa; /* light purple */
}
.main-title {
  background: linear-gradient(90deg, #911370 0%, #f00074 78.37%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.testimonial-card {
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  background: white;
}

.testimonial-text {
  font-size: 14px;
  color: #333;
  line-height: 1.6;
}

.view-link {
  font-size: 14px;
  color: #333;
  text-decoration: underline;
  cursor: pointer;
}
</style>
