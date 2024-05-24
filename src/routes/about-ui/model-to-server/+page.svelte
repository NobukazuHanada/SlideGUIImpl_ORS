<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  let input = $state('');
</script>

<Slide>
  <h1>クライアント・サーバー</h1>
  <p>スタンドアロンの時代は、独自のプロトコルでモデルがサーバーとコミュニケーションしていた</p>
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
      <p>ネットワーク</p>
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
      'f g blank blank i j' 0.5fr
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
    clip-path: polygon(47% 80%, 53% 80%, 50% 100%);
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
