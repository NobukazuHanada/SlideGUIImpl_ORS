<script lang="ts">
  import Slide from '$lib/Slide.svelte';
</script>

<Slide>
  <h1>状態更新伝搬の発展</h1>
  <h2>状態更新伝搬の問題点</h2>
  <ul>
    <li>グリッジの問題 (UIが過剰に更新される)</li>
    <li>余計な再計算を起こす問題</li>
  </ul>
  <h2>発展</h2>
  <ul>
    <li>状態伝搬更新アルゴリズムの様々な提案(MobX, PReact Signals, Reactively)</li>
    <li>更新のスケジューリング</li>
  </ul>
</Slide>
