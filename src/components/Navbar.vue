<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <q-header
    class="q-pa-lg bg-white text-black shadow-sm q-mx-md q-my-md rounded-borders custom-header"
  >
    <q-toolbar class="q-gutter-md justify-between">
      <!-- Logo -->
      <q-img src="~assets/logo.svg" alt="LONGWApps Logo" class="logo" />

      <!-- Navigation Tabs (Desktop) -->
      <div class="row items-center justify-center desktop-nav">
        <q-tabs shrink class="text-grey-8" active-color="black" indicator-color="transparent">
          <q-route-tab v-for="link in links" :key="link.name" no-caps flat style="color: #454545">
            <div class="row items-center no-wrap">
              <span>{{ link.name }}</span>
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
                  v-for="subitem in subitems[link.name] ?? []"
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

      <!-- Hamburger Menu Button (Mobile) -->
      <q-btn flat round icon="menu" class="mobile-nav-toggle" @click="toggleMobileMenu" />

      <!-- Mobile Menu -->
      <q-menu
        v-model="showMobileMenu"
        class="mobile-nav-menu"
        :offset="[0, 8]"
        anchor="top right"
        self="top right"
      >
        <q-list>
          <q-item
            v-for="link in links"
            :key="link.name"
            clickable
            v-close-popup
            @click="subitems[link.name] ? toggleMobileSubmenu(link.name) : goTo(link.url)"
          >
            <q-item-section>{{ link.name }}</q-item-section>
            <q-item-section v-if="subitems[link.name]" side>
              <q-icon
                :name="mobileSubmenuExpanded[link.name] ? 'expand_less' : 'expand_more'"
                size="sm"
              />
            </q-item-section>
          </q-item>

          <!-- Submenus -->
          <q-expansion-item
            v-for="link in linksWithSubitems"
            :key="`sub-${link.name}`"
            v-model="mobileSubmenuExpanded[link.name] as boolean | null"
            dense
            expand-icon="none"
          >
            <q-list dense>
              <q-item
                v-for="subitem in subitems[link.name] ?? []"
                :key="subitem.name"
                clickable
                v-close-popup
                @click="goTo(`${link.url}/${subitem.url}`)"
              >
                <q-item-section class="mobile-subitem">{{ subitem.name }}</q-item-section>
              </q-item>
            </q-list>
          </q-expansion-item>

          <!-- Contact -->
          <q-item clickable v-close-popup @click="goTo('/contact')">
            <q-item-section>Contact Us</q-item-section>
          </q-item>
        </q-list>
      </q-menu>

      <!-- Contact Us Button (Desktop) -->
      <q-btn
        flat
        label="Contact Us"
        :style="{ color: '#5B32A1', fontWeight: 'bold' }"
        class="rounded-borders q-px-md q-py-sm desktop-contact"
        @click="goTo('/contact')"
      >
        <q-img
          src="~assets/icons/message_icon.svg"
          alt="Plane Icon"
          style="width: 20px; margin-left: 6px"
        />
      </q-btn>
    </q-toolbar>
  </q-header>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

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

const subitems = ref<Record<string, Subitem[]>>({
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

// Expanded state (desktop)
const expanded = ref<Record<string, boolean | null>>(
  links.value.reduce<Record<string, boolean | null>>((acc, link) => {
    acc[link.name] = false;
    return acc;
  }, {}),
);

// Expanded state (mobile)
const showMobileMenu = ref(false);
const mobileSubmenuExpanded = ref<Record<string, boolean | null>>(
  links.value.reduce<Record<string, boolean | null>>((acc, link) => {
    acc[link.name] = false;
    return acc;
  }, {}),
);

// Computed property to filter links with subitems
const linksWithSubitems = computed(() =>
  links.value.filter((link) => (subitems.value[link.name]?.length ?? 0) > 0),
);

const toggleMobileMenu = () => {
  showMobileMenu.value = !showMobileMenu.value;
};

const toggleMobileSubmenu = (name: string) => {
  mobileSubmenuExpanded.value[name] = !mobileSubmenuExpanded.value[name];
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
  border-radius: 20px;
}

.custom-header {
  margin-left: 40px;
  margin-right: 40px;
  margin-top: 30px;
  padding-left: 10px;
  padding-right: 10px;
  padding-top: 12px;
  padding-bottom: 12px;
  overflow-x: hidden; /* Prevent horizontal scrollbar */
}

.logo {
  max-width: 150px; /* Default logo size */
}

::v-deep .q-item__section {
  color: #454545 !important;
}

.mobile-subitem {
  padding-left: 20px; /* Indent subitems in mobile menu */
}

.desktop-nav {
  display: flex;
}

.desktop-contact {
  display: flex;
}

.mobile-nav-toggle {
  display: none; /* Hidden by default */
}

.mobile-nav-menu {
  width: 100%;
  max-width: 280px; /* Smaller for better mobile fit */
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  padding: 10px;
}

/* Media Queries for Responsiveness */
@media (max-width: 768px) {
  .custom-header {
    margin-left: 20px;
    margin-right: 20px;
    padding-left: 5px;
    padding-right: 5px;
  }

  .logo {
    max-width: 120px; /* Smaller logo on mobile */
  }

  .desktop-nav {
    display: none; /* Hide desktop nav on mobile */
  }

  .desktop-contact {
    display: none; /* Hide Contact Us button on mobile */
  }

  .mobile-nav-toggle {
    display: block; /* Show hamburger icon only on mobile */
    color: #454545;
  }

  ::v-deep .q-item {
    color: #454545;
    font-size: 14px;
    padding: 10px 16px; /* Consistent padding for mobile menu */
  }

  ::v-deep .mobile-subitem {
    font-size: 13px;
  }
}

@media (max-width: 480px) {
  .custom-header {
    margin-left: 10px;
    margin-right: 10px;
    padding: 8px;
  }

  .logo {
    max-width: 100px;
  }

  .mobile-nav-menu {
    max-width: 250px; /* Even smaller for very small screens */
  }

  ::v-deep .q-item {
    font-size: 12px;
  }

  ::v-deep .mobile-subitem {
    font-size: 11px;
  }
}
</style>
