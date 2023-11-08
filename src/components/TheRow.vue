<script setup>
import { onUpdated, ref, watch } from 'vue';

// const guesses = ref(Array(6).fill(null));
const props = defineProps(['guessedWord']);
const box = ref([]);

console.log('gw', props.guessedWord);

// use a for loop because if word is not guessed it's default is '' and it does not have a length of 5
for (let i = 0; i < 5; i++) {
	box.value.push(props.guessedWord[i]);
}

/*
 * WATCHERS
 */
// watch(props.guessedWord, (newGuessedWord) => {
// 	box.value = [];
// 	for (let i = 0; i < 5; i++) {
// 		box.value.push(newGuessedWord[i]);
// 	}
// });

onUpdated(() => {
	box.value = [];
	for (let i = 0; i < 5; i++) {
		box.value.push(props.guessedWord[i]);
	}
});
</script>

<template>
	<div class="row">
		<div class="box" v-for="char in box" :key="char">
			{{ char }}
		</div>
	</div>
</template>

<style scoped lang="scss">
.row {
	display: flex;
	gap: 10px;
}
.box {
	text-transform: capitalize;
	/* padding: 10px; */
	border: 1px solid #333;
	width: 40px;
	aspect-ratio: 1;
	display: flex;
	justify-content: center;
	align-items: center;

	@media screen and (min-width: 768px) {
		.row {
			width: 60px;
		}
	}
}
</style>
