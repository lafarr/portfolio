<script lang="ts">
	import { GithubIcon, LinkedinIcon, TwitterIcon } from "lucide-svelte";
</script>

<footer class="bg-black/50 backdrop-blur-sm py-8">
	<div class="mx-auto max-w-7xl px-4 text-center">
		<div class="mb-4 flex justify-center gap-4">
			<a href="https://github.com/lafarr" target="_blank" class="text-muted-foreground hover:text-primary">
				<GithubIcon class="h-6 w-6" />
			</a>
			<a href="https://www.linkedin.com/in/james-lafarr-80138a1a3/" target="_blank" class="text-muted-foreground hover:text-primary">
				<LinkedinIcon class="h-6 w-6" />
			</a>
		</div>
		<p class="text-sm text-muted-foreground">
			© {new Date().getFullYear()} James LaFarr. All rights reserved.
		</p>
	</div>
</footer>
