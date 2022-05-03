<template>
    <div class="countdownunit">
        <div class="countdownunit__value">
            {{ value }}
        </div>
        <div>
            {{ unit }}
        </div>
    </div>
</template>

<script>
export default {

    name: "CountdownUnit",

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