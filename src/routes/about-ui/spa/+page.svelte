<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  let input = $state('');
</script>

<Slide>
  <h1>SPA時代</h1>
  <p>Client-Severの時代に逆戻り</p>
  <p>初期ロードが遅い,SEO対策の課題、などのMVC初期化問題が発生する</p>
<p>HTMLがグローバルオブジェクトになってしまう課題、非同期処理、クライアント側でのロジック処理など、JavaScriptがつらくなり、片手間でUIが作れなくなった</p>
  <p></p>
  <div class="input-to-view">
    <div class="a"></div>
    <div class="b"></div>
    <div class="f"></div>
    <div class="g"></div>
    <div class="i"></div>
    <div class="j"></div>
    <div class="m"></div>
    <div class="to-server up-line"></div>
    <div class="to-server down-line"></div>
    <div class="to-server down-triangle"></div>
    <div class="to-server up-triangle"></div>
    <div class="to-server">
      <p>非同期通信, HTTPS, JSON</p>
    </div>
    <div class="controller">
      <h2>Controller</h2>
    </div>

    <div class="view">
      <h2>View</h2>
    </div>

    <div class="model">
      <h2>Model</h2>
      <p>モデルが通信する</p>
    </div>

    <div class="server">
      <h2>Server</h2>
    </div>
  </div>
</Slide>

<style>
  .input-to-view {
    display: grid;
    grid-template:
      'a a server server b b' 1fr
      'a a to-server to-server b b' 1fr
      'a a model model b b' 1fr
      'f g model model i j' 1fr
      'f g blank blank i j' 0.2fr
      'controller controller m m view view';
    text-align: center;
  }

  .controller > div {
    margin: 1rem 0;
  }

  .view p:nth-child(2) {
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
    clip-path: polygon(40% 90%, 60% 90%, 50% 100%);
    transform: translate(-50%, 0);
  }

  .a {
    grid-area: a;
  }

  .b {
    grid-area: b;
  }

  .to-server {
    grid-area: to-server;
    padding: 1rem;
  }

  .to-server.up-line {
    border-left: 1px solid var(--main-color);
    transform: translate(45%, 0);
  }

  .to-server.down-line {
    border-left: 1px solid var(--main-color);
    transform: translate(55%, 0);
  }

  .to-server.up-triangle {
    clip-path: polygon(48% 20%, 52% 20%, 50% 0);
    background-color: var(--main-color);
    transform: translate(5%, 0);
  }

  .to-server.down-triangle {
    clip-path: polygon(48% 80%, 52% 80%, 50% 100%);
    background-color: var(--main-color);
    transform: translate(-5%, 0);
  }

  .server {
    grid-area: server;
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
  }

  .controller,
  .view,
  .model {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
  }
</style>
