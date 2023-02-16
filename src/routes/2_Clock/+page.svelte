<script lang="ts">
	let date = new Date();
	let [hour, minute, second] = [date.getHours(), date.getMinutes(), date.getSeconds()];
	setInterval(() => {
		date = new Date();
		hour = date.getHours();
		minute = date.getMinutes();
		second = second + 1;
	}, 1000);
</script>

<div class="flex flex-col items-center justify-center w-full h-screen bg-slate-800">
	<div
		class="relative w-[400px] h-[400px] rounded-[50%] bg-gradient-to-r from-cyan-400 to-blue-600 drop-shadow-lg"
	>
		<div
			style="transform-origin: 100%; transform: rotate({(hour / 24) * 360 + 90}deg); left: 60px;s;"
			class="absolute w-[140px] top-1/2 h-[8px] rounded-xl bg-white drop-shadow-lg"
		/>
		<div
			style="transform-origin: 100%; transform: rotate({(minute / 60) * 360 + 90}deg); left: 40px;"
			class="absolute w-[160px] top-1/2 h-[6px] rounded-xl bg-white drop-shadow-lg"
		/>
		<div
			style="transform-origin: 100%; transform: rotate({(second / 60) * 360 +
				90}deg); left: 20px; transition: all 0.5s;"
			class="absolute w-[180px] top-1/2 h-[4px] rounded-xl bg-white drop-shadow-lg"
		/>
	</div>
	<div>
		<p class="text-white text-xl mt-3">
			{Intl.DateTimeFormat('en-US', { timeStyle: 'short' }).format(date)}
		</p>
	</div>
</div>
