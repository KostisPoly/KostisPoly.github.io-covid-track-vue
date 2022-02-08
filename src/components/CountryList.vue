<template>
    <b-dropdown :text="selected" variant="outline-info" size="lg" dropright class="m-2">
        <b-dropdown-item v-for="country in countries" :key="country.ID" :value="country.Country" @click="onClick(country)">{{ country.Country }}</b-dropdown-item>
    </b-dropdown>
</template>

<script lang="ts">


export default({
    name: 'CountryList',
    props: ['countries'],
    data() {
        return {
            selected: 'Select Country'
        }
    },
    methods: {
        onClick(country) {
            
            this.selected = country.Country;
            const selectedCountry = this.countries.find((elem) => elem.Country === this.selected)
            this.$emit('set-country', selectedCountry);
        }
    }
})
</script>
