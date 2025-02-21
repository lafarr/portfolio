<script lang="ts">
	import { Button } from "$lib/components/ui/button";

	const navItems = [
		{ href: "#home", label: "Home" },
		{ href: "#projects", label: "Projects" },
		{ href: "#contact", label: "Contact" },
	];
</script>

<header class="flex justify-center fixed left-0 right-0 top-0 z-50 bg-black/40 backdrop-blur-sm">
	<nav class="mx-auto flex h-16 max-w-7xl items-center justify-between px-4">
		<a href="#home" class="text-xl font-bold text-gray-300">JL</a>
		<ul class="flex items-center gap-1">
			{#each navItems as item}
				<li>
					<Button variant="ghost">
						<a class="text-white" href={item.href}>{item.label}</a>
					</Button>
				</li>
			{/each}
		</ul>
	</nav>
</header>
