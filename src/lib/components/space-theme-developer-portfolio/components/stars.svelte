<script lang="ts">
	import { onMount } from "svelte";
	import { fade } from "svelte/transition";

	// Create stars with random positions
	const createStars = () => {
		const stars: { x: number; y: number; delay: number }[] = [];
		for (let i = 0; i < 200; i++) {
			stars.push({
				x: Math.random() * 100,
				y: Math.random() * 100,
				delay: Math.random() * 3,
			});
		}
		return stars;
	};

	let stars = $state(createStars());
	let mounted = $state(false);

	onMount(() => {
		mounted = true;
	});
</script>

{#if mounted}
	<div class="fixed inset-0 overflow-hidden" transition:fade>
		{#each stars as star}
			<div class="absolute h-[2px] w-[2px] rounded-full bg-white" style="left: {star.x}%; top: {star.y}%; animation-delay: {star.delay}s;" />
		{/each}
	</div>
{/if}

<style>
	.absolute {
		animation: twinkle 3s ease-in-out infinite;
	}

	@keyframes twinkle {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0.3;
		}
	}
</style>
