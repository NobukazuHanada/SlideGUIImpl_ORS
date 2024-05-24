<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  const code: string = `c = a + b;
if( c < d ){
    e = c;
}else{
    e = d;
}`;

  const reactiveCode: string = `let a = $state(0); let b = $state(0);
let c = $derived(a + b);
let d = $derived.by(()=> {
  if( c < d ){
    return c;
  }else{
    return d;
  }
})`;
</script>

<Slide>
  <h1>Svelte 5でのReactiviyについて</h1>
  <ul>
    <li>SignalによるReactivtyである</li>
    <li>
      しかし、Reactive
      Programmingのための構文がしっかり用意されており、Signalを直接さわることはない。
    </li>
    <li>リアクティブプログラミングの理想に近い</li>
  </ul>
  <div>
    <div>
      <h2>このようなコードあったとすると</h2>
      <pre><code>{code}</code></pre>
    </div>
    <div>
      <h2>これがSvelteでのReactivity</h2>
      <pre><code>{reactiveCode}</code></pre>
    </div>
  </div></Slide
>

<style>
  div {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  div > div {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
</style>
