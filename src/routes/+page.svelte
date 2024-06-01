<script lang="ts">
	import { AppRail, AppRailTile, AppRailAnchor, Avatar } from '@skeletonlabs/skeleton';

	const tabs = ['HOME', 'PUBLICAÇÕES', 'PESQUISA', 'EQUIPE', 'DIVULGAÇÃO CIENTÍFICA', 'BLOG'];
	let elemCarousel: HTMLDivElement;
	let currentTile: number = 0;
	let y: any = 0;
	let s: number = 0;

	function getY() {
		// console.log(elemCarousel.scrollTop,elemCarousel.scrollTop/elemCarousel.scrollHeight)
		// console.log(elemCarousel.scrollHeight/tabs.length, y, y/elemCarousel.scrollHeight)
		// console.log(elemCarousel.scrollTop, y-80, elemCarousel.scrollTop/(y-80))
		s = Math.round(elemCarousel.scrollTop / (y - 80));
		currentTile = s;
	}
</script>

<svelte:window bind:innerHeight={y} />
<div class="card bg-surface-50-900-token rounded-none h-screen grid grid-cols-[auto_1fr] w-full">
	<AppRail background="bg-surface-50-900-token">
		<svelte:fragment slot="lead">
			<AppRailAnchor href="/"
				><span class="flex justify-center"><Avatar src="/timbu.png" width="w-11" /></span
				></AppRailAnchor
			>
		</svelte:fragment>
		<!-- --- -->
		<span class="flex justify-center items-center flex-col h-full">
			<!-- <AppRailTile bind:group={currentTile} name="tile-3" value={2} title="tile-3"> -->
			<!-- <svelte:fragment slot="lead"> -->
			<span class="[writing-mode:vertical-lr] rotate-180">{tabs[currentTile]}</span>
			<!-- </svelte:fragment> -->
			<!-- <span>Tile 3</span> -->
			<!-- </AppRailTile> -->
		</span>
		<!-- --- -->
		<svelte:fragment slot="trail">
			<AppRailAnchor href="https://github.com/" target="_blank" title="GitHub">
				<span class="flex justify-center">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="50%"
						height="50%"
						viewBox="0 0 24 24"
						{...$$props}
					>
						<path
							fill="currentColor"
							d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5c.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34c-.46-1.16-1.11-1.47-1.11-1.47c-.91-.62.07-.6.07-.6c1 .07 1.53 1.03 1.53 1.03c.87 1.52 2.34 1.07 2.91.83c.09-.65.35-1.09.63-1.34c-2.22-.25-4.55-1.11-4.55-4.92c0-1.11.38-2 1.03-2.71c-.1-.25-.45-1.29.1-2.64c0 0 .84-.27 2.75 1.02c.79-.22 1.65-.33 2.5-.33s1.71.11 2.5.33c1.91-1.29 2.75-1.02 2.75-1.02c.55 1.35.2 2.39.1 2.64c.65.71 1.03 1.6 1.03 2.71c0 3.82-2.34 4.66-4.57 4.91c.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2"
						/>
					</svg>
				</span>
			</AppRailAnchor>
			<span class="flex justify-center mb-8">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="50%"
					height="50%"
					viewBox="0 0 24 24"
					{...$$props}
				>
					<path
						fill="currentColor"
						d="M2 5.995c0-.55.446-.995.995-.995h8.01a.995.995 0 0 1 0 1.99h-8.01A.995.995 0 0 1 2 5.995M2 12c0-.55.446-.995.995-.995h18.01a.995.995 0 1 1 0 1.99H2.995A.995.995 0 0 1 2 12m.995 5.01a.995.995 0 0 0 0 1.99h12.01a.995.995 0 0 0 0-1.99z"
					/>
				</svg>
			</span>
		</svelte:fragment>
	</AppRail>
	<div class="grid place-content-center place-items-center">
		<!-- <span class="badge variant-soft">Tile Value: {currentTile}</span> -->
		<div class="w-[calc(100vw_-_80px)]">
			<div
				bind:this={elemCarousel}
				on:scroll={getY}
				class="[&::-webkit-scrollbar]:hidden [-ms-overflow-style:none] [scrollbar-width:none] h-screen flex flex-col snap-y scroll-py-4 snap-mandatory scroll-smooth flex gap-4 overflow-y-auto px-4 py-10"
			>
				{#each tabs as _}
					<div class="snap-start shrink-0 card h-full w-40 md:w-full text-center">
						{s}
					</div>
				{/each}
			</div>
		</div>
	</div>
</div>
