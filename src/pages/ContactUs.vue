<template>
  <q-page class="bg-gradient">
    <q-img
      :src="frameImage"
      alt="Frame Background"
      class="background-img"
      spinner-color="white"
      :ratio="16 / 9"
    />

    <div class="row q-pa-xl items-center justify-around full-width">
      <!-- Left Section (Text) -->
      <div class="col-12 col-md-6 text-white">
        <h1 class="text-h3 text-bold">Let’s Build Your Dream Product Together</h1>
        <p class="text-subtitle1 q-mt-md">
          Fill in your details, choose a plan, and schedule a free consultation.
        </p>
      </div>

      <!-- Right Section (Form) -->
      <div class="col-12 col-md-6">
        <q-card class="form-card q-pa-lg">
          <q-form @submit.prevent="submitForm">
            <!-- Name & Contact -->
            <div class="row q-col-gutter-md">
              <div class="col-12 col-md-6">
                <label>Name</label>
                <q-input
                  filled
                  v-model="form.name"
                  dense
                  required
                  placeholder="Enter your name"
                  class="white-placeholder"
                />
              </div>
              <div class="col-12 col-md-6">
                <label>Contact Number</label>
                <q-input
                  filled
                  v-model="form.contact"
                  dense
                  required
                  :prefix="countryCode"
                  placeholder="Enter your contact number"
                  class="white-placeholder"
                >
                  <template v-slot:prepend>
                    <q-img
                      src="https://flagcdn.com/w20/lk.png"
                      class="q-mr-sm"
                      style="width: 20px; height: 14px"
                    />
                  </template>
                </q-input>
              </div>
            </div>

            <!-- Email -->
            <div>
              <label>Email Address</label>
              <q-input
                filled
                v-model="form.email"
                class="white-placeholder q-mt-md"
                dense
                required
                type="email"
                placeholder="Enter your email address"
              />
            </div>

            <!-- Idea -->
            <div>
              <label>Tell us about your Idea</label>
              <q-input
                filled
                v-model="form.idea"
                type="textarea"
                class="q-mt-md white-placeholder"
                dense
                required
                placeholder="Describe your idea"
              />
            </div>
            <!-- Product Status -->
            <div>
              <label>Product Status</label>
              <q-select
                filled
                v-model="form.status"
                :options="projectTypes"
                placeholder="Select a project type"
                class="white-placeholder q-mt-md"
                dense
                required
                option-label="label"
                emit-value
                map-options
              />
            </div>
            <!-- Plans -->
            <div class="row q-col-gutter-md q-mt-md">
              <div v-for="plan in plans" :key="plan.name" class="col-6 col-md-3 q-mb-sm">
                <q-card
                  class="plan-card"
                  :class="{ 'plan-selected': form.plan === plan.name }"
                  @click="form.plan = plan.name"
                >
                  <q-card-section>
                    <div class="text-subtitle1 text-bold">{{ plan.name }}</div>
                    <div class="text-caption q-mt-xs">{{ plan.description }}</div>
                    <div class="text-h6 text-bold q-mt-sm">{{ plan.price }}</div>
                  </q-card-section>
                </q-card>
              </div>
            </div>

            <!-- Date & Time -->
            <div class="row q-col-gutter-md q-mt-md">
              <div class="col-12 col-md-6">
                <label>Select Date</label>
                <q-input filled v-model="form.date" dense required placeholder="Select a date">
                  <template v-slot:append>
                    <q-icon name="event" class="cursor-pointer">
                      <q-popup-proxy transition-show="scale" transition-hide="scale">
                        <q-date
                          v-model="form.date"
                          mask="DD/MM/YYYY"
                          color="primary"
                          text-color="white"
                          @update:model-value="(val) => (form.date = val)"
                        />
                      </q-popup-proxy>
                    </q-icon>
                  </template>
                </q-input>
              </div>
              <div class="col-12 col-md-6">
                <label>Select Time</label>

                <q-select
                  filled
                  v-model="form.time"
                  :options="timeOptions"
                  dense
                  required
                  label-color="white"
                />
              </div>
            </div>

            <!-- Submit Button -->
            <div class="q-mt-lg">
              <q-btn
                type="submit"
                unelevated
                label="Schedule a FREE 30 mins Consultation"
                class="full-width text-bold"
                color="primary"
              />
            </div>
          </q-form>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script lang="ts" setup>
import frameImage from 'src/assets/frames/frame-contactus.png';
import { ref } from 'vue';
import { Notify } from 'quasar';

const countryCode = '+94';

const form = ref({
  name: '',
  contact: '02100000005',
  email: '',
  idea: '',
  status: 'Select a project type',
  plan: 'Silver',
  date: '',
  time: '09:00 AM',
});

const projectTypes = [
  { label: 'Mobile App', value: 'Mobile App' },
  { label: 'Web App', value: 'Web App' },
  { label: 'E-Commerce', value: 'E-Commerce' },
  { label: 'SaaS', value: 'SaaS' },
  { label: 'Other', value: 'Other' },
];

const plans = [
  {
    name: 'Silver',
    description: 'Basic features, standard support, up to 3 months.',
    price: '$5,000',
  },
  {
    name: 'Gold',
    description: 'Basic features, standard support, up to 3 months.',
    price: '$10,000',
  },
  {
    name: 'Platinum',
    description: 'Basic features, standard support, up to 3 months.',
    price: '$20,000',
  },
  {
    name: 'Enterprise',
    description: 'Basic features, standard support, up to 3 months.',
    price: 'Custom',
  },
];

const timeOptions = ['09:00 AM', '10:00 AM', '11:00 AM', '02:00 PM', '03:00 PM', '04:00 PM'];

const submitForm = () => {
  Notify.create({
    message: 'Form submitted successfully!',
    color: 'positive',
  });
  form.value = {
    name: '',
    contact: '02100000005',
    email: '',
    idea: 'place holder',
    status: '',
    plan: 'Silver',
    date: '',
    time: '09:00 AM',
  };
};
</script>

<style scoped>
.bg-gradient {
  position: relative;
  min-height: 100vh;
}

.background-img {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  object-fit: cover;
  z-index: -1;
}

.text-white {
  margin-top: -50px;
}

.form-card {
  top: 50px;
  background: #1a0f2e;
  color: white;
  border-radius: 16px;
}

.plan-card {
  cursor: pointer;
  text-align: center;
  background: #2a1f3e;
  color: white;
  border-radius: 12px;
  transition: 0.3s;
}

.plan-card:hover {
  background: #3a2f4e;
}

.plan-selected {
  border: 2px solid #2979ff;
}

.q-input ::v-deep(input),
.q-input ::v-deep(textarea),
.q-input ::v-deep(.q-field__native),
.q-select ::v-deep(.q-field__native),
.q-select ::v-deep(.q-field__input),
.q-icon {
  color: white !important;
}

.q-input,
.q-select {
  background: #2a1f3e;
}

.q-field__control {
  border: none;
}

.white-placeholder ::placeholder {
  color: #ffffff;
  font-family: 'Headings/Normal/Family', sans-serif;
  font-weight: 200;
  font-style: medium;
  font-size: var(--q-headings-normal-size, 16px);
  line-height: 28px;
  letter-spacing: 0%;
}
</style>
