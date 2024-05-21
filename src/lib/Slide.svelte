<script lang="ts">
  import { unmount, type Snippet } from 'svelte';
  let { children }: { children: Snippet; show: boolean } = $props();
</script>

<section>
  {@render children()}
</section>

<style>
  section {
    height: 100%;
    display: grid;
    place-content: center;
    color: white;
    font-size: 1.4em;
    background-color: var(--bg-color);
    grid-row: 1;
    grid-column: 1;
  }
</style>
