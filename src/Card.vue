<template>
    <div ref="cardRef" class="card-wrapper" 
    :class="{
        'is-animated': hasAnimation && isClicked,
    }">
        <div class="card-back"></div>
        <div  class="card-front">
            <span>12</span>
            <img class="clubs-image" src="./images/Clubs.svg" alt="">
        </div>
    </div>
    </template>
<script setup>
import { inject, ref } from 'vue';
import { IS_CLICKED } from './constants.js';

const isClicked = inject(IS_CLICKED);
const cardRef = ref(null);

defineProps({
    hasAnimation: {
        type: Boolean,
        default: false,
    }
})
</script>

<style scoped>
    .clubs-image {
        display: block;
        width: 47px;
    }
    .card-wrapper {
        border: 8px solid white;
        border-radius: 16px;
        width: 184px;
        aspect-ratio: 0.67;
        perspective: 1000px;
        position: relative;
        transition: transform 1s;
        transform-style: preserve-3d;;
    }
    .card-front, .card-back {
        width: 100%;
        height: 100%;
        position: absolute;
        overflow: hidden;
        backface-visibility: hidden;
        transition: transform .6s linear;
        font-weight: 600;
        font-size: 48px;
        line-height: 58px;
        color: black;
    }
    .card-front {
        background-color: white;
        transform: rotateY(180deg);
        flex-direction: column;
    }
    .card-front>*{
        margin-left: 20px;
        margin-bottom: 8px;
    }
    .card-back {
        background: no-repeat url('./images//Pattern.jpg');
    }
    .is-animated {
        animation-name: flipAndPick;
        animation-duration: 1s;
        animation-fill-mode: forwards;
    }

    @keyframes flipAndPick {
        50% {
            transform: rotateY(180deg);
        }
        100% {
            transform: rotateY(180deg) translateY(-370px);
        }
    }
    @media (max-width: 600px) {
        .card-front {
            font-size: 16px;
            line-height: 28px;
        }
        .card-front>*{
            margin-left: 5px;
            margin-bottom: 2px;
        }
        .clubs-image {
            width: 16px;
        }
        .card-wrapper {
            width: 80px;
            border: 4px solid white;
            border-radius: 8px;
        }
        .card-back {
            border-radius: 4px;
            background-position: center;
        }

        @keyframes flipAndPick {
        50% {
            transform: rotateY(180deg);
        }
        75% {
            transform: rotateY(180deg) translateY(-370px);
        }
        100% {
            transform: rotateY(180deg) translateY(-370px) scale(3);
        }
    }
    }
</style>
