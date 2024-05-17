<script lang="ts" setup>
import gsap from 'gsap'
import { defineProps, onMounted, onUnmounted } from 'vue'
const props = defineProps<{
    name: string
    herf: string
    icon: string
}>()
function getImageUrl(name: string) {
    return new URL(`../assets/${name}`, import.meta.url).href
}
let rippleLoad: gsap.Context
onMounted(() => {
    rippleLoad = gsap.context(() => {
        gsap.fromTo('.ripple', {
            duration: 1,
            scale: 0,
            ease: 'power1.inOut',
        }, {
            scale: 1.5

        })

    })
})
function rippleLoadFun() {
    rippleLoad = gsap.context(() => {
        gsap.fromTo('.ripple' + props.name, {
            duration: 0.3,
            scale: 0,
            opacity: 0,
            ease: 'ease.out',
        }, {
            scale: 1.8,
            opacity: 0.4

        })
        gsap.to('.ripple' + props.name, {
            opacity: 0,
            ease: 'ease.out',
            duration: 0.2,
            delay: 0.3
        })
        gsap.to('.launcher_' + props.name, {
            scale: 0.8,
            duration: 0.1,
            ease: 'ease.in'
        })
        gsap.to('.launcher_' + props.name, {
            scale: 1,
            duration: 0.3,
            ease: 'ease.out',
            delay: 0.1
        })

    })
}
onUnmounted(() => {
    rippleLoad.revert()
})

</script>
<template>
    <div class="flex flex-col items-center justify-center rounded-6 overflow-hidden p-8 cursor-pointer relative hover:bg-white hover:bg-op-30 select-none"
        :class="'launcher_' + props.name" @click="rippleLoadFun">
        <div class="bg-white absolute top-1/2 left-1/2 translate-y-[-50%]  translate-x-[-50%] size-40 opacity-0 z-0 rounded-1/2 scale-150"
            :class="'ripple' + props.name">
        </div>
        <img :src="getImageUrl(props.icon)" class="size-16 md:size-24 z-1" :alt="props.icon" draggable="false" />
        <p class="text-center text-sm font-600 z-1">{{ props.name }}</p>
    </div>
</template>