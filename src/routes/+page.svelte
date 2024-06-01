<script lang="ts">
	import {
		AppRail,
		AppRailAnchor,
		Avatar,
		getDrawerStore,
		type DrawerSettings
	} from '@skeletonlabs/skeleton';

	import Scrollwheel from '$lib/Scrollwheel.svelte';
	import data from './data';

	let tabs = data.tabs;
	//const tabs = ['HOME', 'PUBLICAÇÕES', 'PESQUISA', 'EQUIPE', 'DIVULGAÇÃO CIENTÍFICA', 'BLOG'];
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

	const drawerSettings: DrawerSettings = {
		id: 'example-3',
		// Provide your property overrides:
		bgDrawer: 'bg-surface-50-900-token',
		//  bgBackdrop: 'bg-gradient-to-tr from-indigo-500/50 via-purple-500/50 to-pink-500/50',
		bgBackdrop: 'bg-transparent',
		width: 'w-[280px] md:w-[380px]',
		padding: 'pl-20',
		rounded: 'rounded-none'
	};
	const drawerStore = getDrawerStore();
	function drawerOpen(): void {
		drawerStore.open(drawerSettings);
	}
</script>

<svelte:window bind:innerHeight={y} />
<div class="card bg-surface-50-900-token rounded-none h-screen grid grid-cols-[auto_1fr] w-full">
	<AppRail background="bg-surface-50-900-token" class="invisible md:!visible" width="w-0 md:w-20">
		<svelte:fragment slot="lead">
			<AppRailAnchor href="/">
				<span class="flex justify-center"><Avatar src="/timbu.png" width="w-11" /></span>
			</AppRailAnchor>
		</svelte:fragment>
		<!-- --- -->
		<div class="grid grid-rows-2 justify-center h-full gap-1">
			<span class=" flex justify-center items-end">
				<!-- <AppRailTile bind:group={currentTile} name="tile-3" value={2} title="tile-3"> -->
				<!-- <svelte:fragment slot="lead"> -->
				<span class="[writing-mode:vertical-lr] rotate-180 py-4">{tabs[currentTile]}</span>
				<!-- </svelte:fragment> -->
				<!-- <span>Tile 3</span> -->
				<!-- </AppRailTile> -->
			</span>
			<!-- <div class="w-6 h-0.5 bg-gray-400 rounded m-auto"></div> -->
			<div>
				<Scrollwheel {s} h={tabs.length}></Scrollwheel>
			</div>
		</div>
		<!-- div {
			width: 35px;
			height: 5px;
			background-color: black;
			margin: 6px 0;
		  } -->
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

			<button on:click={drawerOpen}>
				<span class="flex justify-center mb-4">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="50%"
						height="50%"
						viewBox="0 0 24 24"
						{...$$props}
					>
						<path
							fill="currentColor"
							d="M20 11H4c-.6 0-1 .4-1 1s.4 1 1 1h16c.6 0 1-.4 1-1s-.4-1-1-1M4 8h16c.6 0 1-.4 1-1s-.4-1-1-1H4c-.6 0-1 .4-1 1s.4 1 1 1m16 8H4c-.6 0-1 .4-1 1s.4 1 1 1h16c.6 0 1-.4 1-1s-.4-1-1-1"
						/>
					</svg>
				</span>
			</button>
		</svelte:fragment>
	</AppRail>

	<div class="grid place-content-center place-items-center">
		<div class="md:hidden flex justify-center items-center">
			<span class="flex justify-center"><Avatar src="/timbu.png" width="w-11" /></span>
			<!-- <AppRailAnchor href="https://github.com/" target="_blank" title="GitHub"> -->
			<span class="flex justify-center">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="3rem"
					height="3rem"
					viewBox="0 0 24 24"
					{...$$props}
				>
					<path
						fill="currentColor"
						d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5c.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34c-.46-1.16-1.11-1.47-1.11-1.47c-.91-.62.07-.6.07-.6c1 .07 1.53 1.03 1.53 1.03c.87 1.52 2.34 1.07 2.91.83c.09-.65.35-1.09.63-1.34c-2.22-.25-4.55-1.11-4.55-4.92c0-1.11.38-2 1.03-2.71c-.1-.25-.45-1.29.1-2.64c0 0 .84-.27 2.75 1.02c.79-.22 1.65-.33 2.5-.33s1.71.11 2.5.33c1.91-1.29 2.75-1.02 2.75-1.02c.55 1.35.2 2.39.1 2.64c.65.71 1.03 1.6 1.03 2.71c0 3.82-2.34 4.66-4.57 4.91c.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2"
					/>
				</svg>
			</span>
			<!-- </AppRailAnchor> -->

			<button on:click={drawerOpen}>
				<span class="flex justify-center items-center md:mb-4">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="3rem"
						height="3rem"
						viewBox="0 0 24 24"
						{...$$props}
					>
						<path
							fill="currentColor"
							d="M20 11H4c-.6 0-1 .4-1 1s.4 1 1 1h16c.6 0 1-.4 1-1s-.4-1-1-1M4 8h16c.6 0 1-.4 1-1s-.4-1-1-1H4c-.6 0-1 .4-1 1s.4 1 1 1m16 8H4c-.6 0-1 .4-1 1s.4 1 1 1h16c.6 0 1-.4 1-1s-.4-1-1-1"
						/>
					</svg>
				</span>
			</button>
		</div>
		<!-- <span class="badge variant-soft">Tile Value: {currentTile}</span> -->
		<div class="w-screen md:w-[calc(100vw_-_80px)]">
			<div
				bind:this={elemCarousel}
				on:scroll={getY}
				class="[&::-webkit-scrollbar]:hidden [-ms-overflow-style:none] [scrollbar-width:none] h-screen flex flex-col snap-y scroll-py-4 snap-mandatory scroll-smooth gap-4 overflow-y-auto px-4 py-10"
			>
				{#each tabs as tab}
					<div id={tab} class="snap-start shrink-0 card h-full md:w-full text-center">
						{s}
					</div>
				{/each}
			</div>
		</div>
	</div>
</div>
