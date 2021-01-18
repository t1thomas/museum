<template>
  <v-app>
    <v-main>
      <MuseumListings />
    </v-main>
  </v-app>
</template>

<script>
import MuseumListings from '@/components/MuseumListings.vue';

export default {
  name: 'App',
  components: {
    MuseumListings,
  },

};
</script>
