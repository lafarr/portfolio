<script lang="ts">
	import {
		Card,
		CardContent,
		CardDescription,
		CardHeader,
		CardTitle,
	} from "$lib/components/ui/card";
	import { Badge } from "$lib/components/ui/badge";
	import { Button } from "$lib/components/ui/button";
	import { GithubIcon, ExternalLinkIcon } from "lucide-svelte";

	type Project = {
		title: string;
		description: string;
		tech: string[];
		github?: string;
		live?: string;
	};

	const projects: Project[] = [
		{
			title: "lazyhttp",
			description:
				"A TUI-based utility that allows acts as an interactive HTTP client.",
			tech: ["Go", "Bubbletea"],
			github: "https://github.com/lafarr/lazyhttp",
		},
		{
			title: "lazyrg",
			description:
				"A TUI-based utility that allows for interactive grepping (using ripgrep).",
			tech: ["Go", "Bubbletea"],
			github: "https://github.com/lafarr/lazyrg",
		},
		{
			title: "Musician Website",
			description:
				"A website for a young musician local to the Upstate NY area.",
			tech: ["Typescript", "Next.js", "Supabase", "PostgreSQL"],
			github: "https://github.com/lafarr/max-lafarr",
			live: "https://maxlafarr.com",
		},
		{
			title: "hierarchy.nvim",
			description:
				"A plugin for Neovim, which recursively displays the call stack; based on the call hierachy functionality in VS Code.",
			tech: ["Lua"],
			github: "https://github.com/lafarr/hierarchy.nvim",
		},
		{
			title: "Metroland Events Calendars",
			description:
				"A collection of calendars for events in the Capital Region, NY area. Built for Metroland Now.",
			tech: ["Next.js", "TailwindCSS", "C#/ASP.NET", "MongoDB"],
			github: "https://github.com/lafarr/metroland-calendars",
			live: "http://3.147.94.95:3000/music-calendar",
		},
	];
</script>

<section id="projects" class="px-4 py-20">
	<div class="mx-auto max-w-7xl">
		<h2 class="mb-12 text-center text-4xl font-bold text-white">
			Recent Work
		</h2>
		<div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each projects as project}
				<Card class="bg-black/50 backdrop-blur-sm">
					<CardHeader>
						<CardTitle>{project.title}</CardTitle>
						<CardDescription>{project.description}</CardDescription>
					</CardHeader>
					<CardContent>
						<div class="mb-4 flex flex-wrap gap-2">
							{#each project.tech as tech}
								<Badge variant="secondary">{tech}</Badge>
							{/each}
						</div>
						<div class="flex gap-2">
							{#if project.github}
								<a href={project.github} target="_blank">
									<Button
										variant="outline"
										size="sm"
										class="gap-2"
									>
										<GithubIcon class="h-4 w-4" />
										GitHub
									</Button>
								</a>
							{/if}
							{#if project.live}
								<a href={project.live} target="_blank">
									<Button
										variant="outline"
										size="sm"
										class="gap-2"
									>
										<ExternalLinkIcon class="h-4 w-4" />
										Live Demo
									</Button>
								</a>
							{/if}
						</div>
					</CardContent>
				</Card>
			{/each}
		</div>
	</div>
</section>
