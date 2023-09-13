<script setup>
    const props = defineProps(['fazConta'])
</script>

<template>
    <div class="row">
        <div class="col text-center pt-5">
            <h2>
                {{ props.fazConta }}
            </h2>
        </div>
    </div>
</template>

<style scoped>
h2 {
    font-size: 100px;
}
</style>