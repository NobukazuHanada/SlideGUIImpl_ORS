<script lang="ts">
  import Slide from '$lib/Slide.svelte';
  import { browser } from '$app/environment';
  const messages = $state([
    { text: 'Hi!', edit: false },
    { text: 'Hello', edit: false },
    { text: 'Bye!', edit: false }
  ]);

  function add() {
    messages.push({ text: 'New Message', edit: false });
  }

  function messageCounts() {
    if (browser && messages.length > 3) {
      alert('messageCounts :' + messages.length);
    }
    return messages.length;
  }

  const code: string = `let messages = $state([
  { text: 'Hi!', edit: false },
  { text: 'Hello', edit: false },
  { text: 'Bye!', edit: false }
]);

function add() {
  messages.push({ text: 'New Message', edit: false });
}

function messageCounts() {
  if (browser) {
    alert('messageCounts :' + messages.length);
   }
   return messages.length;
}


{#each messages as message, i}
    <li>
        {#if message.edit}
            <input type="text" bind:value={message.text} />
            <button onclick={() => (message.edit = false)}>Save</button>
        {:else}
            <span>{message.text}</span>
            <button onclick={() => (message.edit = true)}>Edit</button>
        {/if}
    </li>
{/each}
`;
</script>

<Slide>
  <h1>きめこまやかなReactivity</h1>
  <div>
    <div>
      <pre><code>{code}</code></pre>
    </div>
    <div>
      <div class="messages">
        <p>Messages Update Counts {messageCounts()}</p>
        <button onclick={add}>Add</button>
        {#each messages as message, i}
          {#if message.edit}
            <input type="text" bind:value={message.text} />
            <button onclick={() => (message.edit = false)}>Save</button>
          {:else}
            <span>{message.text}</span>
            <button onclick={() => (message.edit = true)}>Edit</button>
          {/if}
        {/each}
      </div>
    </div>
  </div>
</Slide>

<style>
  div {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 1rem;
  }

  div > div {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .messages {
    display: grid;
    grid-template-columns: 1fr auto;
  }
</style>
