<script lang="ts">
	import { words } from './words';
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';

	let word = '';
	let translated = '';
	let isTranslatedWordVisible = false;

	const gen = () => {
		const entries = Object.entries(words);
		const randomIndex = Math.floor(Math.random() * entries.length);
		const [randomKey, randomValue] = entries[randomIndex];
		word = randomKey;
		translated = randomValue;
		isTranslatedWordVisible = false;
	};

	onMount(gen);
</script>

<div class="h-screen flex items-center justify-center gap-16 lg:flex-row flex-col p-8">
	<p class="font-bold text-5xl">{word.replace('_', ' ')}</p>
	<button
		on:click={() => {
			isTranslatedWordVisible = true;
		}}
		class="relative group font-bold text-5xl"
	>
		{#if !isTranslatedWordVisible}
			<div
				out:fade
				class="absolute top-0 left-0 w-full h-full bg-neutral-800 scale-y-[130%] rounded z-20 hover:scale-y-150 hover:scale-x-[130%] transition"
			/>
		{/if}
		{translated}
	</button>
	<button
		on:click={() => gen()}
		class="fa-solid fa-rotate-right text-5xl hover:scale-125 transition"
	/>
</div>
<div class="fixed top-4 left-4 font-bold text-xl">목요일 창체 자율 발표용</div>

<link
	rel="stylesheet"
	href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
	integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
	crossorigin="anonymous"
	referrerpolicy="no-referrer"
/>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@700&display=swap');
	:root {
		font-family: 'Noto Sans KR', sans-serif;
	}
</style>
