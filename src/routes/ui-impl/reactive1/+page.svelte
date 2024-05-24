<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  const code: string = `c = a + b;
if( c < d ){
    e = c;
}else{
    e = d;
}`;
</script>

<Slide>
  <h1>Reactive Programming</h1>
  <p>次のコードがあったとする</p>
  <pre><code>{code}</code></pre>
</Slide>
