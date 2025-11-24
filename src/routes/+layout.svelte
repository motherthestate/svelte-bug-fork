<script lang="ts">
  import { page } from "$app/state";
  import Link from "$lib/link.svelte"

  let { children } = $props();

  const links = ["/", "/page-1", "/page-2", "/page-3"];
</script>

<div id="pathname">
  svelte page.url.pathname = {page.url.pathname}
</div>

<div id="container">
  <nav>
    {#each links as link}
      <Link href={link} >{link}</Link>
    {/each}
  </nav>
  {@render children()}
</div>

<style>
  #pathname {
    background-color: lightgray;
  }

  #container {
    display: flex;
    gap: 32px;
  }

  nav {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }
</style>
