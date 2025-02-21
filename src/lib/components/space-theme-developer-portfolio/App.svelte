<script lang="ts">
	import Nav from "./components/nav/nav.svelte";
	import Hero from "./components/hero/hero.svelte";
	import Projects from "./components/projects/projects.svelte";
	import Contact from "./components/contact/contact.svelte";
	import Footer from "./components/footer.svelte";
	import Stars from "./components/stars.svelte";
</script>

<div class="dark relative min-h-dvh overflow-hidden bg-black">
	<!-- Animated stars background -->
	<Stars />

	<!-- Layout -->
	<div class="relative z-10 flex min-h-dvh flex-col">
		<Nav />
		<main class="flex-1">
			<Hero />
			<Projects />
			<Contact />
		</main>
		<Footer />
	</div>
</div>

<style>
	:global(html) {
		scroll-behavior: smooth;
	}
</style>
