<template>
  <div class="wrapper">
    <HeroImage />
    <Claim />
    <SearchInput v-model="searchValue" @input="handleInput" />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'App',
  components: {
    HeroImage,
    Claim,
    SearchInput,
  },
  data() {
    return {
      loading: true,
      step: 0,
      searchValue: '',
      results: [],
    };
  },

  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function () {
      console.log(this.searchValue);
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800');
  @import './scss/variables';

  * {
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    margin: 0;
    font-family: 'Montserrat', sans-serif;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    margin: 0;
    padding: 30px;
    width: 100%;
    min-height: 100vh;
  }
</style>
