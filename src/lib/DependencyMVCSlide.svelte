<script lang="ts">
  import Slide from '$lib/Slide.svelte';
  import type { Snippet } from 'svelte';

  let {
    contllerCode,
    modelCode,
    viewCode,
    modelName = '',
    viewName = '',
    firstName = $bindable(''),
    lastName = $bindable(''),
    children
  }: {
    contllerCode: string;
    modelCode: string;
    viewCode: string;
    modelName: string;
    viewName: string;
    firstName: string;
    lastName: string;
    children: Snippet;
  } = $props();
</script>

<Slide>
  <h1>Dependency MVC</h1>
  {@render children()}
  <div class="code-visual-table">
    <div class="controller-code">
      <h2>Contller</h2>
      <pre><code id="js-code">{contllerCode}</code></pre>
    </div>
    <div class="model-code">
      <h2>Model</h2>
      <pre><code id="js-code">{modelCode}</code></pre>
    </div>
    <div class="view-code">
      <h2>View</h2>
      <pre><code id="js-code">{viewCode}</code></pre>
    </div>
    <div class="controller-visual">
      <form>
        <label for="first-name">first name</label>
        <input type="text" id="first-name" bind:value={firstName} />
        <label for="last-name">last name</label>
        <input type="text" id="last-name" bind:value={lastName} />
      </form>
    </div>
    <div class="model-visual">
      <dl>
        <dt>name</dt>
        <dd>{modelName}</dd>
      </dl>
    </div>
    <div class="view-visual">
      <p>name: {viewName}</p>
    </div>
  </div></Slide
>

<style>
  .code-visual-table {
    display: grid;
    grid-template:
      'controller-code controller-visual'
      'model-code model-visual'
      'view-code view-visual';
    gap: 1rem;
  }

  .controller-code {
    grid-area: controller-code;
  }

  .controller-visual {
    grid-area: controller-visual;
    border: 1px solid var(--main-color);
    padding: 1rem;
    border-radius: 5px;
  }

  .model-code {
    grid-area: model-code;
  }

  .model-visual {
    grid-area: model-visual;
    border: 1px solid var(--main-color);
    padding: 1rem;
    border-radius: 5px;
  }

  .view-code {
    grid-area: view-code;
  }

  .view-visual {
    grid-area: view-visual;
    border: 1px solid var(--main-color);
    padding: 1rem;
    border-radius: 5px;
  }

  pre {
    background-color: #333;
    color: #f8f8f2;
    padding: 0.5rem;
    border-radius: 5px;
    overflow: auto;
  }

  code {
    font-family: 'Courier New', Courier, monospace;
    font-size: 1rem;
  }

  input[type='text'] {
    background-color: #333;
    color: var(--text-color);
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 0.5rem;
    font-size: 1rem;
  }

  form {
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
    gap: 0.5rem;
  }

  dl {
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
    gap: 0.5rem;
  }

  dt {
    font-weight: normal;
  }

  dd {
    color: var(--text-color);
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 0.5rem;
    font-size: 1rem;
  }
</style>
