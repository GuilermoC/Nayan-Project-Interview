<template>
    <div class="bulletpoint">
        <h2 class="bulletpoint__number"></h2>
        <h3>{{ title }}</h3>
        <div>{{ description }}</div>
    </div>
</template>

<script>
export default {
    props: {
        title: {
            type: String
        },
        description: {
            type: String
        }
    }
};
</script>

<style lang="scss" scoped>
    @import './BulletPoint.scss';
</style>