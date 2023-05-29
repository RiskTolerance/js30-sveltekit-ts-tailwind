<script lang="ts">
	let color: String = '#5e3fef';
	let colStrength: Number = 0;
	let blurVal: Number = 0;
	let padding: Number | null = 0;
</script>

<div>
	<h2>Hue Shift</h2>
	<input type="color" bind:value={color} name="" id="" />
	<h2>Color Strength</h2>
	<input type="range" bind:value={colStrength} name="" id="" min="0" max="100" />
	<h2>Blur</h2>
	<input type="range" bind:value={blurVal} name="blur" min="0" max="100" />
	<div>
		<h2>Scale Border</h2>
		<input type="range" bind:value={padding} min="0" max="50" />
	</div>
</div>

<div
	style="border-width: {padding}px; border-color: {color};"
	class="relative w-[400px] h-[400px] border-solid"
>
	<div
		style="background-color: {color};opacity: {colStrength}%; mix-blend-mode: hue;"
		class="absolute w-full h-full z-20"
	/>
	<img
		class="absolute w-full h-full z-10"
		style="filter: blur({blurVal}px);"
		src="/src/lib/images/clockbg.jpg"
		alt=""
	/>
</div>
