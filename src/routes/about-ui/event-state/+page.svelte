<script>
  import Slide from '$lib/Slide.svelte';
  import StateMachineDiagram from '$lib/StateMachineDiagram.svelte';
</script>

<Slide>
  <h1>イベントと状態</h1>
  <p>UIにはイベントと状態がある</p>
  <p>Modelだけでなく、Controllerや、Viewにもイベント、ステートがある場合がある</p>
  <p>基本的に状態を網羅して設計するのは実は難しい</p>
  <StateMachineDiagram />
</Slide>
