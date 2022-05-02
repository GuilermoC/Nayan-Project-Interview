<template>
    <div class="">
        <div>
            {{ value }}
        </div>
        <div>{{ unit }}</div>
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: Number
        },
        unit: {
            type: String
        }
    }
};
</script>

<style lang="scss" scoped>
    @import './CountdownUnit.scss';
</style>