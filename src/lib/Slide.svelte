<script lang="ts">
  import { unmount, type Snippet } from 'svelte';
  let { children, className }: { children: Snippet; className?: string } = $props();
</script>

<section class={className}>
  <div>
    {@render children()}
  </div>
</section>

<style>
  section {
    height: 100%;
    place-content: center;
    color: white;
    font-size: 1.4em;
    background-color: var(--bg-color);
    grid-row: 1;
    grid-column: 1;
    padding: 5rem;
  }

  div {
    display: grid;
    place-content: center;
    gap: 1rem;
  }
</style>
