<template>
    <Transition appear @enter="enter" @after-enter="afterEnter">
        <div class="container">
            <div class="card" v-for="card in cards" :key="card.id"></div>
        </div>
    </Transition>
</template>

<script>
import gsap from "gsap";

export default {
    name: "GsapComp",
    components: {
        gsap
    },
    data() {
        return {
            cards: [1, 2, 3, 4, 5, 6]
        }
    },
    methods: {
        enter() {
            gsap.from('.card', {
                repeat: 0,
                duration: 1,
                stagger: .1,
                y: -100,
            })
        },
        afterEnter() {
            console.log('after enter')
        }
    },
}
</script>

<style scoped>
.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    width: 400px;
    margin: 20px auto;
}

.card{
    position: relative;
    z-index: 5;
    width: 50px;
    height: 50px;
    aspect-ratio: 1;
    border-radius: 10px;
    background: blue;
}
</style>