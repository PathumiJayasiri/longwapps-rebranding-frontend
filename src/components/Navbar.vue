<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <q-header class="bg-white text-black shadow-sm q-mx-md q-my-md rounded-borders custom-header">
    <q-toolbar class="q-gutter-md justify-between">
      <!-- Logo -->
      <q-img src="~assets/logo.png" alt="LONGWApps Logo" style="max-width: 200px" />

      <!-- Navigation Tabs Centered -->
      <div class="row items-center justify-center">
        <q-tabs shrink class="text-grey-8" active-color="black" indicator-color="transparent">
          <q-route-tab v-for="link in links" :key="link.name" no-caps flat>
            <div class="row items-center no-wrap">
              <span>{{ link.name }}</span>
              <q-icon
                v-if="subitems[link.name]"
                :name="expanded[link.name] ? 'expand_less' : 'expand_more'"
                style="font-size: 16px; color: #777; margin-left: 4px"
                @click.stop="toggleMenu(link.name)"
              />
            </div>

            <!-- Dropdown Menu -->
            <q-menu
              v-if="subitems[link.name]"
              :model-value="expanded[link.name] ?? false"
              :offset="[0, 8]"
              anchor="bottom left"
              self="top left"
              @before-show="onMenuShow(link.name)"
              @before-hide="onMenuHide(link.name)"
            >
              <q-list>
                <q-item
                  v-for="subitem in subitems[link.name]"
                  :key="subitem.name"
                  clickable
                  v-close-popup
                  @click="goTo(`${link.url}/${subitem.url}`)"
                >
                  <q-item-section>{{ subitem.name }}</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-route-tab>
        </q-tabs>
      </div>

      <!-- Contact Us Button Right -->
      <q-btn
        flat
        label="Contact Us"
        :style="{ backgroundColor: '#7745CD', color: 'white' }"
        class="text-white rounded-borders q-px-md q-py-sm"
        @click="goTo('/contact')"
      >
        <q-img
          src="~assets/paper-plane.png"
          alt="Plane Icon"
          style="width: 20px; margin-left: 6px"
        />
      </q-btn>
    </q-toolbar>
  </q-header>
</template>

<script setup lang="ts">
import { ref } from 'vue';

interface Link {
  name: string;
  url: string;
}
interface Subitem {
  name: string;
  url: string;
}

const links = ref<Link[]>([
  { name: 'Products', url: '/products' },
  { name: 'Services', url: '/services' },
  { name: 'Resources', url: '/resources' },
  { name: 'Careers', url: '/careers' },
]);

const subitems = ref<{ [key: string]: Subitem[] }>({
  Products: [
    { name: 'Product Overview', url: 'product-a' },
    { name: 'Product 1', url: 'product-a' },
    { name: 'Product 2', url: 'product-b' },
  ],
  Services: [
    { name: 'Web Development', url: 'service-a' },
    { name: 'UI/UX Design', url: 'service-a' },
    { name: 'Mobile App Development', url: 'service-a' },
    { name: 'System Integration', url: 'service-a' },
    { name: 'BI Dashboard', url: 'service-b' },
  ],
  Resources: [
    { name: 'Customer Stories', url: 'resource-a' },
    { name: 'Blogs', url: 'resource-a' },
    { name: 'Events', url: 'resource-b' },
  ],
  Careers: [
    { name: 'Open Positions', url: 'job-a' },
    { name: 'Life at LONGWApps', url: 'job-b' },
    { name: 'Meet Our Team', url: 'job-b' },
    { name: 'Instant Apply', url: 'job-b' },
  ],
});

const expanded = ref<{ [key: string]: boolean | null }>(
  links.value.reduce((acc, link) => ({ ...acc, [link.name]: false }), {}),
);

const toggleMenu = (name: string) => {
  expanded.value[name] = !expanded.value[name];
};

const onMenuShow = (name: string) => {
  expanded.value[name] = true;
};

const onMenuHide = (name: string) => {
  expanded.value[name] = false;
};

const goTo = (url: string) => {
  window.location.href = url;
};
</script>

<style scoped>
.rounded-borders {
  border-radius: 8px;
}
.rounded-borders {
  border-radius: 8px;
}

.custom-header {
  padding-left: 10px; /* Left padding */
  padding-right: 10px; /* Right padding */
  padding-top: 12px; /* Top padding */
  padding-bottom: 12px;
  max-width: 1200px; /* Optional: keep navbar contained */
  margin-left: auto;
  margin-right: auto;
}
</style>
