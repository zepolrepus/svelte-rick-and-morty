<script lang="ts">
	import type { Character } from '../models/Character';
	export let character: Character;
</script>

<div class="character">
	<img src={character.image} alt={character.name} />
	<h1>{character.name}</h1>
	<h3>{character.species}</h3>
</div>
