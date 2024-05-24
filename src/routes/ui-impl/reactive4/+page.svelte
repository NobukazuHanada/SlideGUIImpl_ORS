<script>
  import Slide from '$lib/Slide.svelte';
</script>

<Slide>
  <h1>Reactiveまとめと注意点、欠点</h1>
  <h2>リアクティブプログラミングとは</h2>
  <ul>
    <li>入力からの変数の変化の伝搬の仕組み</li>
    <li>変数との制約を構文としてサポート</li>
    <li>入力からの伝搬が一方向</li>
  </ul>
  <h2>注意点、欠点</h2>
  <ul>
    <li>リアクティブ自体の意味がフレームワークによって変わりまくる</li>
    <li>
      双方向の循環依存の制約は基本的にできない
      <ul>
        <li>a,bをリアクティブな変数として、a+b=500 などの制約は不可</li>
      </ul>
    </li>
  </ul>
</Slide>
