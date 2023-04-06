<script lang="ts">
	import '../css/styles.css';

	import type { Character } from '../models/Character';
	import CharacterCard from '../lib/CharacterCard.svelte';

	let page: number = 1;
	let characters: Character[] = [];

	async function loadCharacters() {
		const response = await fetch('https://rickandmortyapi.com/api/character?page=' + page);
		const data = await response.json();
		characters = data.results;
	}

	loadCharacters();

	function nextPage() {
		page++;
		loadCharacters();
	}
	function previousPage() {
		page--;
		loadCharacters();
	}
</script>

<h1 class="title">Rick and Morty</h1>

<div class="container">
	<div class="btns">
		<button on:click={previousPage} disabled={page === 1}>Previous</button>
		<button on:click={nextPage} disabled={page === 42}>Next</button>
	</div>
	<div class="grid">
		{#each characters as character}
			<CharacterCard {character} />
		{/each}
	</div>
</div>
