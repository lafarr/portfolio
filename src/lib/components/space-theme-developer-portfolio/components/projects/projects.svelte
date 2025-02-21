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
      title: "Metroland Events Calendars",
      description:
        "A collection of calendars for events Capital Region, NY area. Built for Metroland Now",
      tech: ["Next.js", "TailwindCSS", "C#/ASP.NET", "MongoDB"],
      github: "https://github.com/lafarr/metroland-calendars",
      live: "http://3.147.94.95:3000/music-calendar",
      image:
        "https://cdn.pixabay.com/photo/2016/07/31/20/54/calendar-1559935_960_720.png",
    },
    {
      title: "Project Two",
      description: "Mobile-first responsive website with smooth animations.",
      tech: ["Svelte", "TailwindCSS"],
      github: "https://github.com",
      image: "https://svelte0.dev/images/ui-placeholder.png",
    },
  ];
</script>

<section id="projects" class="px-4 py-20">
  <div class="mx-auto max-w-7xl">
    <h2 class="mb-12 text-center text-4xl font-bold text-white">
      Recent Projects
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
                  <Button variant="outline" size="sm" class="gap-2">
                    <GithubIcon class="h-4 w-4" />
                    GitHub
                  </Button>
                </a>
              {/if}
              {#if project.live}
                <a href={project.live} target="_blank">
                  <Button variant="outline" size="sm" class="gap-2">
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
