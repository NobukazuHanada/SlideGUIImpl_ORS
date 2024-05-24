<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  const pathlists = ['GET /items', 'GET /items/new', 'POST /item', 'DELETE /cart/1'];
  type Path = 'GET /items' | 'POST /items' | 'GET /items/new';
  let event: Path = $state<Path>('GET /items');
  let itemState: '一覧' | '新規作成' = $derived.by(() => {
    switch (event) {
      case 'GET /items':
        return '一覧';
      case 'GET /items/new':
        return '新規作成';
      case 'POST /items':
        return '一覧';
    }
  });
</script>

<Slide>
  <h1>初期のWeb アプリケーション</h1>
  <ul>
    <li>初期のUIはほぼ、HTMLとHTTP通信によって実現された</li>
    <li>HTML+CSSでView, 入力処理は、HTMLのフォームや、ハイパーリンク、HTTli通信</li>
    <li>
      HTML+CSSの可能な表現のUIしか構築できないが、一方で画面状態管理をしなで良くなり、参入しやすくなった。
    </li>
    <li>サーバー技術者が増え、UIを実装したことがないというエンジニアが爆増した</li>
    <li>Webが発展するにつれて、ユーザーはリッチなインタラクションを求めていった</li>
  </ul>
  <div class="input-to-view">
    <div class="a"></div>
    <div class="b"></div>
    <div class="to-server up-line"></div>
    <div class="to-server down-line"></div>
    <div class="to-server down-triangle"></div>
    <div class="to-server up-triangle"></div>
    <div class="to-server">
      <p>ネットワーク</p>
    </div>

    <div class="view-controller">
      <h2>View+Controller</h2>
      <p>HTMLとCSSの表現に限定された、表示とインタラクション</p>
      <div>
        <label for="event">HTTP</label>
        <select id="event" bind:value={event}>
          <option value="GET /items">GET /items</option>
          <option value="GET /items/new">GET /items/new</option>
          <option value="POST /items">POST /items</option>
        </select>
        <div class="html">
          <p>表示HTML</p>
          <p>{itemState}画面HTML</p>
        </div>
      </div>
    </div>

    <div class="server">
      <h2>Server</h2>
      <p>URLに対応したHTMLを返す</p>
      <div>
        <p>{itemState}状態</p>
      </div>
    </div>
  </div>
</Slide>

<style>
  .input-to-view {
    display: grid;
    grid-template:
      'a a server server b b' 1fr
      'a a to-server to-server b b' 1fr
      'a a view-controller view-controller b b' 1fr;
    text-align: center;
    align-items: center;
  }

  .view-controller {
    grid-area: view-controller;
  }

  .a {
    grid-area: a;
  }

  .b {
    grid-area: b;
  }

  select {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
    background-color: var(--text-background-color);
  }

  select option {
    color: var(--text-color);
    background-color: var(--text-background-color);
  }

  .to-server {
    grid-area: to-server;
    padding: 1rem;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
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

  .server div p {
    padding: 1rem;
    border: 1px solid var(--main-color);
  }

  .view-controller {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    padding: 1rem;
  }

  .view-controller > div {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1rem;
    padding: 1rem;
  }

  .view-controller .html p:last-child {
    padding: 0.5rem;
    border: 1px solid var(--main-color);
  }
</style>
