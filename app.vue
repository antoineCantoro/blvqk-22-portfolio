<template>
  <div>
    <nav>
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/about">About</NuxtLink>
      <NuxtLink to="/project/myproject">My Project</NuxtLink>
    </nav>
      <Transition
        :css="false"
        mode="out-in"
        @enter="enterPageAnim"
        @leave="leavePageAnim"
      > 
        <div :key="route.name" :data-page="route.name">
          <NuxtPage/>
        </div>
      </Transition>

      <Overlay :routeName="route.name"/>
  </div>
</template>

<script setup>
  import { gsap } from "gsap";
  const route = useRoute();

  onMounted(() => {
    // console.log(route);
    // console.log(currentRoute.name);
  })
  
  function leavePageAnim(pageEl, done) {
    // console.log(pageEl);
    // console.log(route)
    // console.log("<- ${ route.name } : leave");

    gsap.timeline()
        .to(".overlay", {transformOrigin: "bottom center", scaleY: 1, duration: 1, ease: "expo.inOut"})
        .to(".overlay span", {y: "0%", duration: 0.5, ease: "power3.out", onComplete: () => {done()}}, '-=0.25')
  }

  function enterPageAnim(pageEl, done) {
    // console.log(pageEl);
    // console.log(`enter: ${ route.name } ->`);
    // done();

    gsap.timeline()
        .to(".overlay span", {y: "-100%", duration: 0.5, delay: 1, ease: "power3.out", clearProps: true})
        .to(".overlay", {transformOrigin: "top center", scaleY: 0,  onComplete: () => {done()}}, '-=0.25')
  }
</script>