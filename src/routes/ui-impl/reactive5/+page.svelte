<script>
  import Slide from '$lib/Slide.svelte';
</script>

<Slide>
  <h1>Reactiveのフレームワークやライブラリ</h1>
  <h2>Reactive Programmingとその他のライブラリについて</h2>
  <ul>
    <li>
      Rx, Svelte, Solid, vue.js, MobXなど様々なフレームワークでReactive
      Programmingがサポートされている
    </li>
    <li>ただし「変数の伝搬システム」のみのサポートが多い</li>
    <li>RxはObservable, SvelteやSolidはSignalの仕組みで「変数の伝搬システム」を構築する</li>
    <li>
      RxやSolidは、制約を記述するためのAPIがむき出しであり、本来なら構文としてシンプルになるべき
    </li>
    <li>Svelteはわりと素直にReactiveが書きやすいようになっている</li>
  </ul>

  <h2>Functional Reactive Programmingに関して</h2>
  <p>
    リアクティブオブジェクトに更に「明示的な連続時間」で、型の制約をつけて、更に強い制約を加えたもの。（ただし、オレオレFRPが出てきて、発案者がFRPと言わずにDCTPと言ってたりする。）
  </p>
</Slide>
