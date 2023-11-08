<script setup>
import TheRow from '../components/TheRow.vue';
import { ref, watchEffect } from 'vue';

/*
 * STATE
 */
const guesses = ref(Array(6).fill(null));
const currentGuess = ref('');
// const guesses = ref(['Hello', 'World', null, null, null, null]);

/*
 * HANDLERS
 */
function setGuesses(value) {
	const positionToReplace = guesses.value.findIndex((val) => val === null);
	guesses.value[positionToReplace] = value;
}

function setCurrentGuess(value) {
	currentGuess.value += value;
}

/*
 * COMPUTED
 */
//  const isCurrent =

/*
 * WATCHERS
 */
watchEffect(() => {
	window.addEventListener('keydown', function (event) {
		console.log(event.key);
		console.log('cg', currentGuess.value);
		if (event.key === 'Enter') {
			setGuesses(currentGuess.value);
			console.log('asdsa', guesses.value);
			currentGuess.value = '';
			return;
		}
		if (currentGuess.value.length >= 5) {
			return;
		}
		setCurrentGuess(event.key);
	});
});
</script>

<template>
	<main>
		<TheRow
			v-for="(guess, index) in guesses"
			:key="guess"
			:guessed-word="
				index === guesses.findIndex((val) => val == null)
					? currentGuess
					: guess ?? ' '
			"
		/>
	</main>
</template>

<style lang="scss" scoped>
main {
	display: flex;
	flex-direction: column;
	gap: 10px;
}
</style>
