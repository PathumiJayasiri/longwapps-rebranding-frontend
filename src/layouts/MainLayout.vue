<template>
  <q-layout view="lHh Lpr lFf">
    <Navbar />

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- ✅ Plain footer component, not <q-footer> -->
    <AppFooter />
  </q-layout>
</template>

<script setup lang="ts">
import Navbar from 'components/Navbar.vue';
import AppFooter from 'components/AppFooter.vue'; // renamed to AppFooter inside file
</script>
