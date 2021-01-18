<template>
  <v-expand-transition>
  <div
    v-if="show"
    class="news-overlay transition-fast-in-fast-out "

  >
    <div class="news-overlay__header">
      <h1>News</h1>
      <h3 v-if="newsDate">{{newsDate}}</h3>
    </div>

    <p>
      {{ newsObj.title}}
    </p>
  </div>
  </v-expand-transition>

</template>

<script>
export default {
  name: 'NewsOverlay',
  props: ['newsObj', 'show'],
  computed: {
    newsDate() {
      // eslint-disable-next-line no-prototype-builtins
      if (this.newsObj.hasOwnProperty('date')) {
        const date = new Date(this.newsObj.date);
        return date.toLocaleString('en-GB', { year: 'numeric', month: 'numeric', day: 'numeric' });
      }
      return null;
    },
  },
};
</script>

<style scoped>

.news-overlay {
  background: rgba(25, 124, 124, 0.31);
  padding: 0.5rem;
  height: 200px;
}

.news-overlay__header {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}
.news-overlay__header h1{
  text-decoration: underline;
}
.news-overlay__header h3{
  text-align: end;
  font-style: italic;
}
</style>
