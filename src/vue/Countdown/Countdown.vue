<template>
    <div class="banner">
        <div class="container">
            <div class="row row--countdown bg bg--dark">
                <h1>{{ title }}</h1>
            </div>
            
            <CountdownUnit  value=15 unit='days' />

        </div>
    </div>
</template>

<script>
// Made a seperate component for each countdown unit
import CountdownUnit from "../CountdownUnit/CountdownUnit.vue";

export default {
    components: {
        CountdownUnit
    },

    props: {
        title: {
            type: String
        }
    }

    // TODO: add countdown logic
};
</script>

<style lang="scss" scoped>
    @import './Countdown.scss';
</style>