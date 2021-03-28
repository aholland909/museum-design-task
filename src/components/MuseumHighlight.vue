<template>
  <div class="museum-highlight">
    <!-- Display the available information for the highlight -->
    <div v-for="highlight in spaceHighlights" :key="highlight.ID">
      <div class="museum-highlight__card">
        <div class="museum-highlight__iconcircle">
          <font-awesome-icon
            class="museum-highlight__icon"
            :icon="getIcon(highlight.name)"
          />
        </div>
        <img
          :src="
            highlight.image
              ? ''
              : 'https://bulma.io/images/placeholders/128x128.png'
          "
          class="museum-highlight__image"
        />
        <div class="museum-highlight__content">
          <p class="museum-highlight__title">
            {{ highlight.name.toUpperCase() }}
          </p>
          <p class="museum-highlight__description">
            {{ highlight.description }}
          </p>
          <div v-if="highlight.news">
            <p class="museum-highlight__title"> News </p>
            <p class="museum-highlight__title"> {{highlight.news.title}}</p>
          </div>
          <div v-if="highlight.quiz">
            <a :href="highlight.quiz">Want to try our quick quiz?</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MuseumHighlight",
  components: {},
  mixins: [],
  props: {
    spaceHighlights: {
      type: Array,
    },
  },
  data() {
    return {};
  },
  computed: {
    newsDate() {
      // Highlight's news item date
      return null;
    },
  },
  created() {
    this.spaceHighlights = this.sortCards(this.spaceHighlights);
  },
  methods: {
    //sort hightlight by datatime
    sortCards(highlights) {
      let sortedHighlights = highlights;
      sortedHighlights.sort((a, b) => {
        return new Date(a.date) - new Date(b.date);
      });

      return sortedHighlights;
    },
    //get logo!
    getIcon(title) {
      var logo = {
        Asteroids: "meteor",
        Planets: "globe-europe",
        Comets: "meteor",
        "Meteor showers": "shower",
      };

      if (logo[title]) {
        return logo[title];
      }

      return "meteor";
    },
  },
};
</script>

<style lang="scss">
.museum-highlight {
  color: black;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;

  &__card {
    position: relative;
    display: flex;
    flex-direction: column;
    border-color: lightblue;
    border-style: solid;
    margin: 1rem;
    height: 400px;
    width: 400px;
  }
  &__iconcircle {
    height: 25px;
    width: 25px;
    background-color: #bbb;
    border-radius: 50%;
    position: absolute;
    top: -15px;
    right: -15px;
  }
  &__icon {
    display: flex;
    margin: auto;
    margin-top: 2px;
  }
  &__image {
    height: 200px;
    width: 100%;
  }
  &__content {
    padding: 0rem 1rem;
  }

  &__title {
    color: lightblue;
  }

  &__description {
    color: lightblue;
  }
}
</style>


