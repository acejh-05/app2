<script setup>
    import Box from './Quadrant.vue';
    import myButton from './Button.vue';
    import { ref } from 'vue';

    let word = ref("SIGMA")
    function changeWord() {
        if (word.value === "SIGMA") {
            word.value = "ALPHA";
        } else if (word.value === "ALPHA") {
            word.value = "SIGMA";
        }
    }

    let isActive = ref(false)
    function changeColor() {
        if (isActive.value === false) {
            isActive.value = true;
        } else if (isActive.value === true)
            isActive.value = false;
    }
    
</script>

<template>
    <div class="grid">
        <box class="top-left">
            <p>{{ word }}</p>
        </box>
        <box class="top-right"></box>
        <box class="bottom-left">
            <div class="image">
                <img src="/Users/acenjhite/Desktop/client-side-code/app2/public/mcgregor_crest_coat_of_arms.png" alt="coat of arms">
            </div>
        </box>
        <box class="bottom-right">
            <div class="diamond">
                <div class="topTri" :class=" { active : isActive }"></div>
                <div class="bottomTri" :class="{ active : isActive }"></div>
            
                <div class="buttons">
                    <myButton class ="topButton" :action="changeWord">
                        <div class="topLabel">A</div>
                    </myButton>
                    <myButton class ="bottomButton" :action="changeColor">
                        <div class="bottomLabel">B</div>
                    </myButton>
                </div>
            </div>
        </box>
    </div>

</template>

<style scoped>
    .grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        gap: 10px;
        margin: 10px;
        height: calc(100vh - 20px);
    }

    .top-right {
        border-top-right-radius: 100%;
    }

    .image {
        animation: spin 15s infinite linear;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        33%,
        100% { transform: rotate(360deg); }
    }

    .top-left {
        font-family: "Exile", system-ui;
        font-weight: 400;
        font-style: normal;
        font-size: 64px;
    }

    .diamond {
        position: relative;
    }

    .topTri {
        border-left: 50px solid transparent;
        border-right: 50px solid transparent;
        border-bottom: 100px solid #dc143c;
        width: 0;
        height: 0;
        position: relative;
        display: block;
    }

    .bottomTri {
        border-left: 50px solid transparent;
        border-right: 50px solid transparent;
        border-top: 100px solid #dc143c;
        width: 0;
        height: 0;
        position: relative;
        display: block;
    }

    .topButton {
        position: absolute;
        top: 0%;
        right: 0%;
        clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
    }

    .bottomButton {
        position: absolute;
        top: 50%;
        right: 0%;
        clip-path: polygon(0% 0%, 100% 0%, 50% 100%);
    }
    
    .topTri.active {
        animation: rainbow 2s infinite linear;
    }

    .bottomTri.active {
        animation: rainbow 2s infinite linear;
    }

    @keyframes rainbow {
        from {
            filter: hue-rotate(0deg) 
        } to {
            filter: hue-rotate(360deg);
        }
    }

</style>
