<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  let input = $state('');
</script>

<Slide>
  <h1>入力と表示</h1>
  <p>UIを対話だと考えれば、入力に対する、応答を返している</p>
  <p>入力を解釈して出力していると見なすことができる</p>
  <div class="input-to-view">
    <div class="f"></div>
    <div class="g"></div>
    <div class="h"></div>
    <div class="i"></div>
    <div class="j"></div>
    <div class="m"></div>
    <div class="controller">
      <h2>入力</h2>
      <p>ユーザーが入力する</p>
      <div>
        <input id="input" type="text" bind:value={input} />
      </div>
    </div>

    <div class="view">
      <h2>表示</h2>
      <p>ユーザーに見せる</p>
      <p>{input}</p>
    </div>
  </div>
</Slide>

<style>
  .input-to-view {
    display: grid;
    grid-template:
      'f g h i j'
      'controller controller m view view';
  }

  .controller > div {
    margin: 1rem 0;
  }

  .view p:nth-child(3) {
    margin: 1rem 0;
  }

  .controller {
    grid-area: controller;
  }

  .view {
    grid-area: view;
  }

  .g {
    grid-area: g;
    border-left: 1px solid var(--main-color);
    border-top: 1px solid var(--main-color);
    height: 3rem;
  }

  .h {
    grid-area: h;
    border-top: 1px solid var(--main-color);
  }

  .i {
    grid-area: i;
    border-top: 1px solid var(--main-color);
    border-right: 1px solid var(--main-color);
  }

  .j {
    background-color: var(--main-color);
    clip-path: polygon(47% 80%, 53% 80%, 50% 100%);
    transform: translate(-50%, 0);
  }

  .controller,
  .view {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
  }
</style>
