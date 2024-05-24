<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  let input = $state('');
</script>

<Slide>
  <h1>モデル</h1>
  <p>入力と表示以外の機能を考えてみよう</p>
  <p>アプリ本来の状態や処理が含まれているのが分かる</p>
  <div class="input-to-view">
    <div class="f"></div>
    <div class="g"></div>
    <div class="i"></div>
    <div class="j"></div>
    <div class="m"></div>
    <div class="controller">
      <h2>入力</h2>
      <p>ユーザーが入力する</p>
      <div>
        <label for="input">10 + 10 =</label>
        <input id="input" type="text" bind:value={input} />
      </div>
    </div>

    <div class="view">
      <h2>表示</h2>
      <p>ユーザーに見せる</p>
      <p>{input == '10' ? '正解' : '不正解'}</p>
    </div>

    <div class="model">
      <h2>モデル</h2>
      <p>アプリの状態や処理</p>
      <p>入力情報:{input != '' ? input : '0'} = 20を判定する</p>
    </div>
  </div>
</Slide>

<style>
  .input-to-view {
    display: grid;
    grid-template:
      'a a model b b' 1fr
      'f g model i j' 1fr
      'f g blank i j' 0.5fr
      'controller controller m view view';
  }

  .controller > div {
    margin: 1rem 0;
  }

  .view p:nth-child(2) {
    margin: 1rem 0;
  }

  .model p:nth-child(2) {
    margin: 1rem 0;
  }

  .controller {
    grid-area: controller;
  }

  .view {
    grid-area: view;
  }

  .model {
    grid-area: model;
  }
  .g {
    grid-area: g;
    border-left: 1px solid var(--main-color);
    border-top: 1px solid var(--main-color);
  }

  .i {
    grid-area: i;
    border-top: 1px solid var(--main-color);
    border-right: 1px solid var(--main-color);
  }

  .j {
    grid-area: j;
    background-color: var(--main-color);
    clip-path: polygon(47% 80%, 53% 80%, 50% 100%);
    transform: translate(-50%, 0);
  }

  .controller,
  .view,
  .model {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
  }
</style>
