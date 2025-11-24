<script lang="ts">
  import type { SvelteHTMLElements } from 'svelte/elements';
  import { page } from '$app/state';
  import type { Merge } from 'ts-essentials';

  let {
    href,
    children,
    ...anchorProps
  }: Merge<
    SvelteHTMLElements['a'],
    {
      href: string;
      stateHrefs?: string[];
    }
  > = $props();

  const activeStart = $derived(page.url.pathname.startsWith(href));
</script>

<a
  href={href}
  {...anchorProps}
  class={['group/link focus', anchorProps.class]}
  data-page={page.url.pathname}
  data-active={activeStart ? 'true' : undefined}
>
  {@render children?.()} {page.url.pathname}
</a>


<style>
  a[data-active="true"] {
    background-color: lime;
  }

  a:not([data-active="true"]):hover {
    background-color: lightgray;
  }
</style>
