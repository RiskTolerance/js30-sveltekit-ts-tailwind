<script lang="ts">
	type KV = { [key: string]: string };
	const drumArray: KV = {
		a: 'clap',
		s: 'hihat',
		d: 'kick',
		f: 'openhat',
		g: 'boom',
		h: 'ride',
		j: 'snare',
		k: 'tom',
		l: 'tink'
	};

	function handleKeyPress(e: KeyboardEvent) {
		const match = document.querySelector(`.${e.key}`);
		if (match) {
			const audio = new Audio(`/src/lib/sound/${drumArray[e.key]}.wav`);
			audio.play();
			match.classList.add('scale-105');
			match.classList.replace('border-blue-700', 'border-blue-500');
			setTimeout(() => {
				match.classList.replace('border-blue-500', 'border-blue-700');
				match.classList.remove('scale-105');
			}, 100);
		}
		return null;
	}
</script>

<svelte:window on:keydown|preventDefault={handleKeyPress} />

<div
	class="flex items-center justify-center h-screen w-full overflow-hidden bg-[url('/src/lib/images/drum-kit.jpg')] bg-cover"
>
	<div class="flex flex-row space-x-5">
		{#each Object.entries(drumArray) as [key, text]}
			<div
				class="{key} flex flex-col items-center w-24 h-24 p-4 border-4 border-blue-700 rounded-md bg-slate-600 text-white"
			>
				<kbd class="font-bold">{key.toUpperCase()}</kbd>
				<span class="font-thin">{text.toUpperCase()}</span>
			</div>
		{/each}
	</div>
</div>
