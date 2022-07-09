<template>
    <div class="overlay">
        <div class="overlay-content-wrapper"><span>{{ props.routeName }}</span></div>
    </div>
</template>
<script setup>
    const props = defineProps({
        routeName: String
    })
</script>
<style>
.overlay {
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    background-color: #1d1d1d;
    color: white;
    z-index: 100;

    transform: scaleY(0);
    transform-origin: bottom center;

    display: flex;
    align-items: center;
    justify-content: center;
}

.overlay-content-wrapper {
    overflow: hidden;
}

span {
    display: block;
    transform: translateY(100%);

    /* transform-origin: top left; */

    font-size: 24px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>