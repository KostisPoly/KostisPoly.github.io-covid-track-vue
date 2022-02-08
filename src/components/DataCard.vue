<template>
    <b-card-group deck>
        <b-card bg-variant="light" text-variant="dark" :title= "region" class="m-5 text-center">
            <b-card-text>
                Last Update:  {{ formatDate }}
            </b-card-text>
        </b-card>
        <b-card bg-variant="primary" text-variant="light" title="Cases Reported" class="m-5 text-center">
            <b-card-text v-if="!stats.ID">
                NEW: {{ formatNumber(global.NewConfirmed)}} - TOTAL: {{ formatNumber(global.TotalConfirmed)}}
            </b-card-text>
            <b-card-text v-else>
                NEW: {{ formatNumber(stats.NewConfirmed)}} - TOTAL: {{ formatNumber(stats.TotalConfirmed)}}
            </b-card-text>
        </b-card>
        <b-card bg-variant="secondary" text-variant="light" title="Deaths Reported" class="m-5 text-center">
            <b-card-text v-if="!stats.ID">
                NEW: {{ formatNumber(global.NewDeaths)}} - TOTAL: {{ formatNumber(global.TotalDeaths)}}
            </b-card-text>
            <b-card-text v-else>
                NEW: {{ formatNumber(stats.NewDeaths)}} - TOTAL: {{ formatNumber(stats.TotalDeaths)}}
            </b-card-text>
        </b-card>
    </b-card-group>
    
</template>

<script>
import dayjs from 'dayjs';
import numeral from 'numeral';

export default ({
    name: 'DataCard',
    props: ['date', 'stats', 'global', 'region'],
    computed: {
        formatDate: function() {
            return dayjs(this.date).format('dddd, MMMM D, YYYY h:mm A');
        }
    },
    methods: {
        formatNumber(num) {
            return numeral(num).format('0,0');
        }
    }
})
</script>
