<script setup>
    import { defineProps } from 'vue';
    const props = defineProps({
        action: Function,
        isActive: Boolean,
    })

    function atClick() {
        props.action();
    }
</script>

<template>
    <div class="myButton">
        <button class="buttons" @click="atClick">
            <slot></slot>
        </button>  
    </div>
</template>

<style scoped>
    .buttons {
        cursor: pointer;
        display: block;
        color: white;
        background: none;
        border: none;
        font-size: 20px;
        font-family: Arial, Helvetica, sans-serif;
        width: 100px;
        height: 100px;
    }
</style>