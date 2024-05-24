<script>
  import Slide from '$lib/Slide.svelte';
</script>

<Slide>
  <h1>Observable</h1>
  <ul>
    <li>ObservableはReactiveをサポートするための仕組みの一つ</li>
    <li>Dependency MVCのM-V間の更新伝搬パターン（Observerパターン）をReactiveにも展開しもの</li>
    <li>変数同士の制約が非常に書きにくい。購読忘れなどが発生する</li>
    <li>更新伝搬の仕組みも未発達</li>
  </ul>
</Slide>
