<script>
  import Slide from '$lib/Slide.svelte';

  let showIndex = $state(0);
</script>

<Slide>
  <h1>インタラクション</h1>
  <h2>インタラクションはそもそも対話</h2>
  <button onclick={() => (showIndex = (showIndex + 1) % 7)}>対話をすすめる</button>
  <div class="dialog">
    <p>ユーザ</p>
    <p>システム</p>
    <p class:show={showIndex >= 1}>Aをカートにいれて</p>
    <p class:show={showIndex >= 2}>OK!カートにいれました</p>
    <p class:show={showIndex >= 3}>Bをカートにいれて</p>
    <p class:show={showIndex >= 4}>OK!カートにいれました</p>
    <p class:show={showIndex >= 5}>カートの中身は？</p>
    <p class:show={showIndex >= 6}>カートの中身はAとBです</p>
  </div>
</Slide>

<style>
  .dialog {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .dialog p {
    border: 1px solid var(--text-background-color);
    border-radius: 5px;
    padding: 0.5rem;
  }

  .dialog p:first-child,
  .dialog p:nth-child(2) {
    background-color: var(--text-background-color);
    color: white;
    display: block;
  }

  .dialog p:nth-child(odd) {
    text-align: left;
    justify-self: start;
  }
  .dialog p:nth-child(even) {
    text-align: right;
    justify-self: end;
  }
  .dialog p:not(:first-child, :nth-child(2)) {
    transition:
      transform 0.5s ease-in-out,
      opacity 0.5s ease-in-out;
    transform: translate(0, 100%);
    opacity: 0;
  }
  .dialog p.show {
    opacity: 1;
    transform: translate(0, 0);
  }
</style>
