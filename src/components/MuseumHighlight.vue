<template>
  <v-card
        :class="`card ${highlight.isThirdParty ? 'card--api-data' : 'card--mus-data'}`"
        max-width="400"
      >
        <i class="card__badge fa fa-star fa-2x"></i>

        <v-img
          class="white--text align-end"
          height="200px"
          :src="`https://source.unsplash.com/featured/?${highlight.name}`"
        >
          <news-overlay v-if="hasNews" :show="hover" :news-obj="highlight.news" />

        </v-img>
        <div class="card__body">
          <div class="card__header">
            <h2> {{ highlight.name}} </h2>
            <v-btn
              @mouseenter="hover = true"
              @mouseleave="hover = false"
              v-if="hasNews"
              icon
              small
              fab
            >
            <v-icon
            >
              mdi-information
            </v-icon>
            </v-btn>
          </div>

          <div class="card__text">
            <p>{{ highlight.description}}</p>
          </div>
        </div>

      </v-card>
</template>

<script>
import NewsOverlay from '@/components/NewsOverlay.vue';

export default {
  name: 'MuseumHighlight',
  components: {
    NewsOverlay,
  },
  mixins: [
  ],
  props: {
    highlight: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      hover: false,
    };
  },
  computed: {
    hasNews() {
      // eslint-disable-next-line no-prototype-builtins
      return this.highlight.hasOwnProperty('news');
    },
    // newsDate() {
    //   // Highlight's news item date
    // },
  },
  methods: {

  },
  created() {

  },
};
</script>

<style lang="scss" scoped>
.museum-highlight {

}
.card {
  position: relative;
  margin-bottom: 1rem;
  margin-left: 1rem;
}
.card__header {
  padding: 0.6rem;
  display: flex;
  justify-content: space-between;
}
.card__text {
  font-size: medium;
  padding: 0.5rem;

}
.card__badge {
  position: absolute;
  right: -15px;
  top: -15px;
  color: #fac548;
  z-index: 99;
}

.card--api-data {
  background-color: #dea286 !important;
}
.card--mus-data {
  background-color: #785f8ea6 !important;
}
</style>
