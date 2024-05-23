<script lang="ts">
  import { goto, onNavigate } from '$app/navigation';
  import { page } from '$app/stores';
  import { fly, fade, scale } from 'svelte/transition';
  import 'destyle.css';
  let { children } = $props();

  onNavigate(async (navigation) => {
    if (!document.startViewTransition) return;

    return new Promise((resolve) => {
      document.startViewTransition(async () => {
        resolve();
        await navigation.complete;
      });
    });
  });
</script>

<nav>
  <ul>
    {#each [{ href: '/', name: 'title' }, { href: '/page1', name: 'p1' }] as { href, name }}
      <li><a class:current={$page.url.pathname === href} {href}>{name}</a></li>
    {/each}
  </ul>
</nav>

<main>
  <div
    class="page-container"
    in:fly={{ x: 100, duration: 1000 }}
    out:fly={{ x: -100, duration: 1000 }}
  >
    {@render children()}
  </div>
</main>

<style>
  :root {
    --bg-color: #051725;
    --nav-bg-color: #0a4c78;
    --main-color: #6fb4ff;
    --accent-color: #e1fc17ed;
    --text-color: #fffbfbf5;
    --nav-text-size: 1rem;
  }
  :global(body, html) {
    height: 100%;
    font-family: 'Arial', 'メイリオ';
  }

  :global(body) {
    min-height: 100%;
    display: grid;
    grid-template-rows: auto 1fr;
    overflow-x: hidden;
    margin: 0;
    background-color: black;
  }

  :global(h1) {
    color: var(--main-color);
    font-size: 5rem;
  }

  :global(p) {
    color: var(--text-color);
    font-size: 1.5rem;
  }

  nav {
    view-transition-name: header;
    background-color: var(--nav-bg-color);
    box-shadow: 0 10px 25px 0 rgba(0, 0, 0, 0.5);
  }

  ul {
    display: flex;
    gap: 0.5rem;
    list-style: none;
    padding: 1rem;
  }

  a {
    text-decoration: none;
    color: var(--text-color);
    font-size: var(--nav-text-size);
  }

  a.current {
    color: var(--accent-color);
  }

  main {
    background-color: black;
    display: grid;
  }

  .page-container {
    grid-row: 1;
    grid-column: 1;
  }

  @keyframes fade-in {
    from {
      opacity: 0;
    }
  }

  @keyframes fade-out {
    to {
      opacity: 0;
    }
  }

  @keyframes slide-from-right {
    from {
      transform: translateX(50%);
    }
  }

  @keyframes slide-to-left {
    to {
      transform: translateX(-50px);
    }
  }

  :root::view-transition-old(root) {
    animation:
      300ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
      500ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
  }

  :root::view-transition-new(root) {
    animation:
      210ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
      300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
  }
</style>
