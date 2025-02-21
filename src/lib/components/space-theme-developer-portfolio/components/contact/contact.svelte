<script lang="ts">
	import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "$lib/components/ui/card";
	import { Input } from "$lib/components/ui/input";
	import { Textarea } from "$lib/components/ui/textarea";
	import { Button } from "$lib/components/ui/button";
	import { Label } from "$lib/components/ui/label";

	let name = $state("");
	let email = $state("");
	let message = $state("");
	let isSubmitting = $state(false);

	const handleSubmit = async (e: SubmitEvent) => {
		e.preventDefault();
		isSubmitting = true;
		// Simulate API call
		await new Promise((resolve) => setTimeout(resolve, 1000));
		// Reset form
		name = "";
		email = "";
		message = "";
		isSubmitting = false;
	};
</script>

<section id="contact" class="px-4 py-20">
	<div class="mx-auto max-w-xl">
		<Card class="bg-black/50 backdrop-blur-sm">
			<CardHeader>
				<CardTitle>Get in Touch</CardTitle>
				<CardDescription>Send me a message and I'll get back to you soon.</CardDescription>
			</CardHeader>
			<CardContent>
				<form onsubmit={handleSubmit} class="flex flex-col gap-4">
					<div class="grid gap-2">
						<Label for="name">Name</Label>
						<Input id="name" bind:value={name} placeholder="Your name" disabled={isSubmitting} required />
					</div>
					<div class="grid gap-2">
						<Label for="email">Email</Label>
						<Input id="email" type="email" bind:value={email} placeholder="your@email.com" disabled={isSubmitting} required />
					</div>
					<div class="grid gap-2">
						<Label for="message">Message</Label>
						<Textarea id="message" bind:value={message} placeholder="Your message..." disabled={isSubmitting} required />
					</div>
					<Button type="submit" disabled={isSubmitting}>
						{isSubmitting ? "Sending..." : "Send Message"}
					</Button>
				</form>
			</CardContent>
		</Card>
	</div>
</section>
