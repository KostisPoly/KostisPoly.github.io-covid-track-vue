<template>
<!-- As a heading -->
    <b-navbar toggleable type="dark" variant="dark">
        <b-navbar-brand tag="h1" class="mb-10">CovidStats</b-navbar-brand>
        <b-navbar-toggle target="navbar-toggle-collapse">
        <template #default="{ expanded }">
            <b-icon v-if="expanded" icon="chevron-bar-up"></b-icon>
            <b-icon v-else icon="chevron-bar-down"></b-icon>
        </template>
        </b-navbar-toggle>

        <b-collapse id="navbar-toggle-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
            <b-nav-item href="https://covid19api.com/" target="blank">Data provided by covid19.com</b-nav-item>
        </b-navbar-nav>
        </b-collapse>
    </b-navbar>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            expanded: false
        }
    }
};
</script>
