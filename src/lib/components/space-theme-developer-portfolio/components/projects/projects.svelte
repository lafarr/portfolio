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
		image: string;
	};

	const projects: Project[] = [
		{
			title: "Musician Website",
			description:
				"A website for a young musician local to the Upstate NY area.",
			tech: ["Typescript", "Next.js", "Supabase", "PostgreSQL"],
			github: "https://github.com/lafarr/max-lafarr",
			live: "https://maxlafarr.com",
			image: "https://cdn.pixabay.com/photo/2014/04/03/11/35/microphone-311918_960_720.png",
		},
		{
			title: "hierarchy.nvim",
			description:
				"A plugin for Neovim, which recursively displays the call stack; based on the call hierachy functionality in VS Code.",
			tech: ["Lua"],
			github: "https://github.com/lafarr/hierarchy.nvim",
			image: "https://cdn.pixabay.com/photo/2017/05/12/15/16/hexagon-2307350_960_720.png",
		},
		{
			title: "Metroland Events Calendars",
			description:
				"A collection of calendars for events in the Capital Region, NY area. Built for Metroland Now.",
			tech: ["Next.js", "TailwindCSS", "C#/ASP.NET", "MongoDB"],
			github: "https://github.com/lafarr/metroland-calendars",
			live: "http://3.147.94.95:3000/music-calendar",
			image: "https://cdn.pixabay.com/photo/2016/07/31/20/54/calendar-1559935_960_720.png",
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
						<img
							src={project.image}
							alt={project.title}
							class="mb-4 h-48 w-full rounded-lg object-contain"
						/>
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
