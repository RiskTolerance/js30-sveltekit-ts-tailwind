<script lang="ts">
	import FlexPanel from '../../lib/ui/FlexPanel.svelte';

	let textGrid = [
		{
			id: 'a',
			words: ['performant', 'code', 'today'],
			imgUrl: 'code'
		},
		{
			id: 'b',
			words: ['color', 'and', 'type'],
			imgUrl: 'typography'
		},
		{
			id: 'c',
			words: ['our', 'creativity', 'shines'],
			imgUrl: 'creative-shine'
		},
		{
			id: 'd',
			words: ['founded', 'in', 'experience'],
			imgUrl: 'exp'
		},
		{
			id: 'e',
			words: ['aesthetic', 'harmony', 'forever'],
			imgUrl: 'zen'
		}
	];
</script>

<div class="flex flex-row w-full h-screen justify-evenly bg-slate-400 overflow-clip">
	{#each textGrid as grid}
		<FlexPanel props={grid} />
	{/each}
</div>
