<script lang="ts">
	export let tabs;
</script>

<nav class="list-nav py-2">
	<ul>
		{#each tabs as tab}
			<li><a href="/#{tab}">{tab}</a></li>
		{/each}
		<!-- <li><a href="/">Homepage</a></li>
		<li><a href="/about">About</a></li>
		<li><a href="/blog">Blog</a></li>
		<li><a href="/contact">Contact</a></li> -->
	</ul>
</nav>
