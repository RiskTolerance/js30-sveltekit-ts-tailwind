<script lang="ts">
	import { fade } from 'svelte/transition';
	import { fly } from 'svelte/transition';
	interface Data {
		id: string;
		words: string[];
		imgUrl: string;
	}

	export let props: Data;
	let visible = false;
	let expand = (event: any) => {
		const target = document.querySelector(`#${event.originalTarget.id}`);
	};
</script>

<div
	id={props.id}
	on:mouseenter={() => {
		visible = true;
	}}
	on:mouseleave={() => {
		visible = false;
	}}
	style="background-image: url(/images/{props.imgUrl}.jpg);"
	class="flex flex-col w-1/5 hover:w-3/5 justify-around items-center transition-all bg-cover text-stone-100 font-bold text-4xl"
>
	{#if visible}
		<p
			class="drop-shadow-lg"
			in:fly={{ y: -200, duration: 500 }}
			out:fly={{ y: -200, duration: 200 }}
		>
			{props.words[0]}
		</p>
	{/if}

	<p class="drop-shadow-lg">{props.words[1]}</p>

	{#if visible}
		<p
			class="drop-shadow-lg"
			in:fly={{ y: 200, duration: 500 }}
			out:fly={{ y: 200, duration: 200 }}
		>
			{props.words[2]}
		</p>
	{/if}
</div>
