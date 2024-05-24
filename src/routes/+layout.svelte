<script lang="ts">
  import { goto, onNavigate } from '$app/navigation';
  import { page } from '$app/stores';
  import { fly, fade, scale } from 'svelte/transition';
  import 'destyle.css';
  import '../app.css';
  import { browser } from '$app/environment';
  let { children } = $props();
  let gotoPrevPage = $state(false);

  const links = [
    { href: '/', name: 'title' },
    { href: '/about', name: 'about' },
    { href: '/agenda', name: 'agenda' },
    { href: '/about-ui/what-is-ui', name: 'what-is-ui' },
    { href: '/about-ui/why-difficult-ui', name: 'why-difficult-ui' },
    { href: '/about-ui/deal-with-difficulty', name: 'deal-with-difficulty' },
    { href: '/about-ui/historical-transition', name: 'historical-transition' },
    { href: '/about-ui/interaction', name: 'interaction' },
    { href: '/about-ui/input-to-view', name: 'input-view' },
    { href: '/about-ui/model', name: 'model' },
    { href: '/about-ui/model-to-server', name: 'model-server' },
    { href: '/about-ui/event-state', name: 'state' },
    { href: '/about-ui/first-web-app', name: 'first-web-app' },
    { href: '/about-ui/spa', name: 'spa' },
    { href: '/about-ui/state-framework-and-mvc', name: 'state-framework-and-mvc' },
    { href: '/ui-impl', name: 'ui-impl' },
    { href: '/ui-impl/dependency-mvc', name: 'mvc' },
    { href: '/ui-impl/dependency-mvc-1', name: 'mvc1' },
    { href: '/ui-impl/dependency-mvc-2', name: 'mvc2' },
    { href: '/ui-impl/dependency-mvc-3', name: 'mvc3' },
    { href: '/ui-impl/reactive', name: 'reactive' },
    { href: '/ui-impl/reactive1', name: 'reactive1' },
    { href: '/ui-impl/reactive2', name: 'reactive2' },
    { href: '/ui-impl/reactive3', name: 'reactive3' },
    { href: '/ui-impl/reactive4', name: 'reactive4' },
    { href: '/ui-impl/reactive5', name: 'reactive5' },
    { href: '/ui-impl/observable', name: 'observable' },
    { href: '/ui-impl/propagation-development', name: 'propagation-development' }
  ];

  let currentPageIndex = $derived.by(() => {
    let index = links.findIndex((link) => link.href === $page.url.pathname);
    return index === -1 ? 0 : index;
  });

  onNavigate(async (navigation) => {
    if (!document.startViewTransition) return;

    return new Promise((resolve) => {
      document.startViewTransition(async () => {
        resolve();
        await navigation.complete;
      });
    });
  });

  function handleKeyDown(event: KeyboardEvent) {
    if (event.key === 'ArrowLeft' && currentPageIndex > 0) {
      gotoPrevPage = false;
      goto(links[currentPageIndex - 1].href);
    } else if (event.key === 'ArrowRight' && currentPageIndex < links.length - 1) {
      gotoPrevPage = true;
      goto(links[currentPageIndex + 1].href);
    }
  }

  function handleNavClick(i: number) {
    gotoPrevPage = i < currentPageIndex;
  }
</script>

<svelte:window on:keydown={handleKeyDown} />

<nav>
  <ul>
    {#each links as { href, name }, i}
      <li>
        <a class:current={$page.url.pathname === href} onclick={() => handleNavClick(i)} {href}
          >{name}</a
        >
      </li>
    {/each}
  </ul>
</nav>

<main class:goto-prev={gotoPrevPage}>
  <div
    class="page-container"
    in:fly={{ x: 100, duration: 1000 }}
    out:fly={{ x: -100, duration: 1000 }}
  >
    {@render children()}
  </div>
</main>

<style>
  nav {
    view-transition-name: header;
    background-color: var(--nav-bg-color);
    box-shadow: 0 10px 25px 0 rgba(0, 0, 0, 0.5);
  }

  nav ul {
    display: flex;
    gap: 0.5rem;
    list-style: none;
    padding: 0.5rem;
    flex-wrap: wrap;
  }

  nav ul a {
    text-decoration: none;
    color: var(--text-color);
    font-size: var(--nav-text-size);
  }

  nav ul a.current {
    color: var(--accent-color);
  }

  main {
    background-color: black;
    display: grid;
    view-transition-name: next-page;
  }

  main.goto-prev {
    view-transition-name: prev-page;
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
      transform: translateX(30%);
    }
  }

  @keyframes slide-to-left {
    to {
      transform: translateX(-30%);
    }
  }

  @keyframes slide-from-left {
    from {
      transform: translateX(-30%);
    }
  }

  @keyframes slide-to-right {
    to {
      transform: translateX(30%);
    }
  }

  :root::view-transition-old(prev-page) {
    animation:
      300ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
      500ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
  }

  :root::view-transition-new(prev-page) {
    animation:
      210ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
      300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
  }

  :root::view-transition-old(next-page) {
    animation:
      300ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
      500ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-right;
  }

  :root::view-transition-new(next-page) {
    animation:
      210ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
      300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-left;
  }
</style>
