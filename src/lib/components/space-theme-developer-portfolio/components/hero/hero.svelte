<script lang="ts">
	import { fade, fly } from "svelte/transition";
</script>

<section id="home" class="flex min-h-[80vh] items-center justify-center px-4 py-20">
	<div class="text-center" in:fade>
		<h1 class="gradient-text mb-6 text-6xl font-bold sm:text-7xl md:text-8xl" in:fly={{ y: 50, duration: 1000 }}>James LaFarr</h1>
		<p class="text-xl text-muted-foreground" in:fly={{ y: 50, duration: 1000, delay: 200 }}>Software Engineer</p>
	</div>
</section>

<style>
	.gradient-text {
		background: linear-gradient(to right, #ff0000, #ff4000, #ff8000, #ffbf00, #ffff00, #80ff00, #00ff00, #00ffff, #0080ff, #0000ff, #4b0082, #8f00ff, #ff00ff, #ff0080, #ff0000);
		-webkit-background-clip: text;
		background-clip: text;
		color: transparent;
		animation: rainbow 12s linear infinite;
		background-size: 300% auto;
	}

	@keyframes rainbow {
		0% {
			background-position: 0% 50%;
		}
		50% {
			background-position: 100% 50%;
		}
		100% {
			background-position: 0% 50%;
		}
	}
</style>
