<script lang="ts">
	export let s: number = 0;
	export let h: number;
	let x: number, y: number, z: number;
	let length: number = h;

	$: {
		// x = Math.round((length / h) * s);
		y = Math.round((length / h) * s);
		// z = Math.round((length / h) * s);
		// console.log(x, y, z, s, h);
	}
</script>

<div class="flex flex-col items-center gap-1.5">
	{#each Array.from({ length }) as _, i}
		{#if y === 0}
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-7={y === i} class:!bg-black={y === i} />
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-6={y === i} />
			<div class="w-5 h-[3px] bg-gray-400 rounded" />
		{:else if y === h - 1}
			<div class="w-5 h-[3px] bg-gray-400 rounded" />
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-6={y === i} />
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-7={y === i} class:!bg-black={y === i} />
		{:else}
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-6={y === i} />
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-7={y === i} class:!bg-black={y === i} />
			<div class="w-5 h-[3px] bg-gray-400 rounded" class:w-6={y === i} />
		{/if}
		<!-- <div class="w-5 h-[3px] bg-gray-400 rounded" class:w-6={z === i + 1} /> -->
	{/each}
</div>
