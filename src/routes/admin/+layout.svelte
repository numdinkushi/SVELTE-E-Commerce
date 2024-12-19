<script lang="ts">
  import { page } from "$app/stores";
  import Nav from "$lib/components/Nav.svelte";
  import { cn } from "$lib/utils";
  import type { PageData } from "./$types";

  let pathname = $derived($page.url.pathname);
  let {children} = $props();

  // let { data }: { data: PageData } = $props();
</script>

<Nav>
  {@render navLink({ href: "/admin", text: "Dashboard" })}
  {@render navLink({ href: "/admin/products", text: "Products" })}
  {@render navLink({ href: "/admin/users", text: "Users" })}
  {@render navLink({ href: "/admin/orders", text: "Orders" })}
</Nav>

<div class="container my-6">
  {@render children()}
</div>

{#snippet navLink({ href, text }: { href: string; text: string })}
  <a
    {href}
    class={cn(
      "p-4 capitalize hover:bg-secondary hover:text-secondary-foreground focus-visible:bg-secondary focus-visible:text-secondary-foreground",
      pathname === href && "bg-background text-foreground"
    )}>{text}</a
  >
{/snippet}
