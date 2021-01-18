<template>
  <div class="museum-listings">
    <div class="header">
    <h1>Space</h1>
    </div>
    <div class="highlights" >
      <MuseumHighlight
        v-for="highlight in sorted"
        :highlight="highlight"
        :key="highlight.id"
      />
    </div>

  </div>
</template>

<script>

import MuseumHighlight from '@/components/MuseumHighlight.vue';

export default {
  name: 'MuseumListings',
  components: {
    MuseumHighlight,
  },
  mixins: [],
  props: {},
  data() {
    return {
      spaceHighlights: [
        {
          date: '2020-04-20 12:20:00',
          description: 'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
          id: 1,
          image: '',
          name: 'Asteroids',
        },
        {
          date: '2020-05-20 15:50:00',
          description: 'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
          id: 9,
          image: '',
          name: 'Comets',
        },
        {
          date: '2020-05-01 9:22:00',
          description: 'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
          id: 7,
          image: '',
          name: 'Planets',
          news: {
            date: '2020-08-18 18:00:00',
            title: 'Attend our talk about Jupiter with Dr. Hogarth',
          },
        },
        {
          date: '2020-07-05 4:10:00',
          description: 'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
          id: 12,
          image: '',
          name: 'Meteor showers',
          news: {
            title: 'The Lyrids will peak at on April 21-22 2021, at night',
          },
        },
      ],
      spacePartners: {
        832: {
          date: '2020-06-01 11:45:00',
          description: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.',
          image: '',
          name: 'Mauna Kea Observatories',
        },
      },
    };
  },
  computed: {
    combine() {
      const combined = [];
      // add museum data
      this.spaceHighlights.forEach((el) => {
        const currEl = el;
        // set third party boolean
        currEl.isThirdParty = false;
        combined.push(currEl);
      });
      // add api data
      Object.keys(this.spacePartners).forEach((key) => {
        const currObj = this.spacePartners[key];
        // set third party boolean
        currObj.isThirdParty = true;
        combined.push(currObj);
      });
      return combined;
    },
    sorted() {
      const { combine } = this;
      // assign unique id based on element's index in array
      // eslint-disable-next-line no-param-reassign,no-return-assign
      combine.forEach((data, idx) => data.id = idx + 1);
      return combine.sort((a, b) => new Date(a.date) - new Date(b.date));
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  padding: 20px;
}
.highlights {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-flow: wrap;
}
</style>
