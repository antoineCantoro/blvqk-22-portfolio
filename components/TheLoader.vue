<template>
    <div class="loader">
        <div class="loader-content-wrapper"><span>{{ currentHello }}</span></div>
    </div>
</template>
<script setup>
    import { gsap } from "gsap";

    let currentHello = ref("Hello")

    const helloArray = ["Hello", "Bonjour", "Holà", "Annyông", "Hej", "Ciao", "Zdravei", "Jeje", "Salü", "Hallo", "Cześć", "Živjo", "Pryvit", "Yasou", "Kóyo"]

    onMounted(() => {
        console.log("loader ready to be launched");
        let helloInterval = setInterval(() => {
            currentHello.value = helloArray[ Math.floor( Math.random() * helloArray.length ) ];
        }, 100)

        gsap.timeline()
            .to(".loader span", {y: "-100%", delay: 4, onComplete: () => { clearInterval(helloInterval) }})
            .to(".loader", {scaleY: 0})
    })
</script>
<style>
.loader {
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    background-color: #1d1d1d;
    color: white;
    z-index: 110;

    transform-origin: top center;

    display: flex;
    align-items: center;
    justify-content: center;
}

.loader-content-wrapper {
    overflow: hidden;
}

.loader-content-wrapper > span {
    display: block;
    /* transform: translateY(100%); */

    /* transform-origin: top left; */

    font-size: 24px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>