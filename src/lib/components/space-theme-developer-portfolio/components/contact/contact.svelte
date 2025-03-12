<script lang="ts">
  import {
    Card,
    CardContent,
    CardDescription,
    CardHeader,
    CardTitle,
  } from "$lib/components/ui/card";
  import { Input } from "$lib/components/ui/input";
  import { Textarea } from "$lib/components/ui/textarea";
  import { Button } from "$lib/components/ui/button";
  import { Label } from "$lib/components/ui/label";

  let name = $state("");
  let email = $state("");
  let message = $state("");
  let isSubmitting = $state(false);
  let formSuccess = $state(false);
  let formError = $state(false);

  const handleSubmit = (event) => {
    event.preventDefault(); // This is still needed to prevent the default form submission

    isSubmitting = true;

    const form = event.target;
    const formData = new FormData(form);

    fetch("https://api.web3forms.com/submit", {
      method: "POST",
      body: formData,
    })
      .then((response) => response.json())
      .then((data) => {
        if (data.success) {
          formSuccess = true;
          // Clear form fields
          name = "";
          email = "";
          message = "";
        } else {
          formError = true;
        }
      })
      .catch((error) => {
        console.error("Error:", error);
        formError = true;
      })
      .finally(() => {
        isSubmitting = false;
      });

    return false;
  };
</script>

<section id="contact" class="px-4 py-20">
  <div class="mx-auto max-w-xl">
    <Card class="bg-black/50 backdrop-blur-sm">
      <CardHeader>
        <CardTitle>Get in Touch</CardTitle>
        <CardDescription
          >Send me a message and I'll get back to you soon.</CardDescription
        >
      </CardHeader>
      <CardContent>
        <form
          id="contactForm"
          action="https://api.web3forms.com/submit"
          method="POST"
          class="flex flex-col gap-4"
          onsubmit={handleSubmit}
        >
          {#if formSuccess}
            <div class="mt-4 p-4 bg-green-100 text-green-700 rounded">
              Your message has been sent successfully!
            </div>
          {/if}

          {#if formError}
            <div class="mt-4 p-4 bg-red-100 text-red-700 rounded">
              There was an error sending your message. Please try again.
            </div>
          {/if}
          <input
            type="hidden"
            name="access_key"
            value="16baa0f1-bdd0-4376-80af-2f4fc6b56103"
          />

          <!-- Add this line to use the form submitter's email as the reply-to address -->
          <input type="hidden" name="replyto" id="replyto" bind:value={email} />

          <div class="grid gap-2">
            <Label for="name">Name</Label>
            <Input
              id="name"
              name="name"
              bind:value={name}
              placeholder="Your name"
              disabled={isSubmitting}
              required
            />
          </div>
          <div class="grid gap-2">
            <Label for="email">Email</Label>
            <Input
              id="email"
              name="email"
              type="email"
              bind:value={email}
              placeholder="your@email.com"
              disabled={isSubmitting}
              required
            />
          </div>
          <div class="grid gap-2">
            <Label for="message">Message</Label>
            <Textarea
              id="message"
              name="message"
              bind:value={message}
              placeholder="Your message..."
              disabled={isSubmitting}
              required
            />
          </div>
          <Button type="submit" disabled={isSubmitting}>
            {isSubmitting ? "Sending..." : "Send Message"}
          </Button>
        </form>
      </CardContent>
    </Card>
  </div>
</section>
