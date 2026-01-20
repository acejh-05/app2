<script setup>
    defineProps ({
        variant: {
            type: String,
            default: ""
        }
    })
</script>

<template>
    <div class="box">
        <slot></slot>
    </div>
</template>

<style scoped>
    .box {
        background-color: #dcdcdc;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>