<template>
  <div id="app">
    <!-- Header -->
    <AppHeader />

    <!-- Main Content -->
    <div ref="works" id="works-section">
      <Works @show-artwork="showArtwork" />
    </div>

    <div ref="about" id="about-section">
      <About />
    </div>

    <!-- Artwork Modal -->
    <ArtworkModal v-if="showModal" :artwork="selectedArtwork" @close="closeModal" />
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';
import AppHeader from './components/HeaderSection.vue';
import Works from './components/WorksSection.vue';
import About from './components/AboutSection.vue';
import ArtworkModal from './components/ArtworkModal.vue';

export default {
  components: {
    AppHeader,
    Works,
    About,
    ArtworkModal
  },
  setup() {
    const showModal = ref(false);
    const selectedArtwork = ref(null);

    const showArtwork = (artwork: any) => {
      selectedArtwork.value = artwork;
      showModal.value = true;
    };

    const closeModal = () => {
      showModal.value = false;
    };

    return { showModal, selectedArtwork, showArtwork, closeModal };
  }
};
</script>

<style>
@import './assets/main.css';
/* Importing the global styles */
</style>
