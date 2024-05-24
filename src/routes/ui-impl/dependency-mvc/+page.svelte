<script>
  import Slide from '$lib/Slide.svelte';
</script>

<Slide>
  <h1>Dependency MVC</h1>
  <ul>
    <li>Model, View, Controllerに分ける</li>
    <li>Contollerがモデルを更新</li>
    <li>モデルが変更をViewに通知</li>
    <li>モデルを参照する複数のViewに一貫性が保たれる</li>
  </ul>
</Slide>
