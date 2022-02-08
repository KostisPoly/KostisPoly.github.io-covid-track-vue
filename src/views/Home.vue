<template>
  <div class="home">
    <div v-if="!loading">
      <DataCard :date= date :stats= stats :countries= countries :global= global :region= region />
      <CountryList :countries= countries @set-country="selectedCountry" />
    </div>
    <div v-else class="d-flex justify-content-center m-5">
      <b-spinner type="grow" variant="secondary"></b-spinner>
      <b-spinner type="grow" variant="primary"></b-spinner>
      <b-spinner type="grow" variant="success"></b-spinner>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import DataCard from '@/components/DataCard';
import CountryList from '@/components/CountryList';

export default {
  name: 'Home',
  components: {
    DataCard,
    CountryList
  },
  methods: {
    async fetchData() {
      const res = await fetch('https://api.covid19api.com/summary')
      const  data = await res.json()
      return data;
    },
    selectedCountry(country) {
      this.stats = country;
      this.region = country.Country;
    }
  },
  data() {
    return {
      loading: true,
      date: '',
      stats: {},
      countries: [],
      global: {},
      region: 'Global'
    };
  },
  async created() {
    const data = await this.fetchData();
    this.date = data.date;
    this.stats = {};
    this.countries = data.Countries;
    this.global = data.Global;
    this.loading = false;
  }
}
</script>

<style scoped>
  .spinner-grow.text-secondary {
    /* animation-delay: 0.1s; */
    animation-duration: 0.7s;
  }
  .spinner-grow.text-primary {
    /* animation-delay: 0.3s; */
    animation-duration: 0.8s;
  }
  .spinner-grow.text-success {
    /* animation-delay: 0.6s; */
    animation-duration: 0.9s;
  }
</style>