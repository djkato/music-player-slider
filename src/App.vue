<template>
	<div
		@mouseup="is_toggled = !is_toggled"
		:class="[is_toggled ? 'player_body_pop_in' : 'player_body_pop_out']"
		class="h-14 w-14 bg-purple-600 fixed bottom-12 right-12 rounded-full flex justify-end pr-2 items-center scale-100 hover:animate-[speaker-hover_0.3s_ease-in-out_1_forwards] active:brightness-110 speaker-active z-10"
	>
		<div v-show="is_toggled"></div>
		<SpeakerWaveIcon class="h-10 w-10 text-white -scale-x-100"></SpeakerWaveIcon>
	</div>
</template>

<script setup>
import { ref } from "vue"
import { SpeakerWaveIcon } from "@heroicons/vue/24/solid"
const is_toggled = ref(false)
</script>

<style>
.player_body_pop_in {
	animation: player-body-pop-in 1s forwards 1 ease-in-out;
}

.player_body_pop_out {
	animation: player-body-pop-out 1s forwards 1 ease-in-out;
}

.speaker-active:active {
	transform: scale(1.3) !important;
}
@keyframes player-body-pop-in {
	0% {
		@apply w-14;
	}
	100% {
		@apply w-[80vw];
	}
}
@keyframes player-body-pop-out {
	0% {
		@apply w-[80vw];
	}
	100% {
		@apply w-14;
	}
}
@keyframes speaker-hover {
	0% {
		transform: scale(1);
	}
	25% {
		transform: scale(0.8);
	}
	50% {
		transform: scale(1.25);
	}
	100% {
		transform: scale(1.2);
	}
}
</style>
