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
  <h1>Reactive Programming2</h1>
  <p>変数同士の関係を見ると次のようになる</p>
  <div class="code-and-visual">
    <pre><code>{code}</code></pre>
    <div class="visual">
      <p class="box-a">a</p>
      <p class="box-b">b</p>
      <p class="box-c">c</p>
      <p class="box-d">d</p>
      <p class="box-e">e</p>
      <div class="a-c"></div>
      <div class="b-c"></div>
      <div class="c-e"></div>
      <div class="d-e"></div>
    </div>
  </div>
</Slide>

<style>
  .code-and-visual {
    display: flex;
    gap: 1rem;
  }

  .visual {
    display: grid;
    grid-template:
      'blank1 box-a blank2 box-b blank3 blank3'
      'blank1 a-c box-c b-c box-d blank6'
      'blank1 blank7 c-e box-e d-e blank8';
  }

  .box-a {
    grid-area: box-a;
  }

  .box-b {
    grid-area: box-b;
  }

  .box-c {
    grid-area: box-c;
  }

  .box-d {
    grid-area: box-d;
  }
  .box-e {
    grid-area: box-e;
  }

  .a-c {
    grid-area: a-c;
    border-bottom: 1px solid var(--main-color);
    border-left: 1px solid var(--main-color);
    transform: translate(50%, -50%);
    z-index: 1;
  }

  .b-c {
    grid-area: b-c;
  }

  .c-e {
    grid-area: c-e;
  }

  .d-e {
    grid-area: d-e;
  }

  .a-c,
  .c-e {
    border-bottom: 1px solid var(--main-color);
    border-left: 1px solid var(--main-color);
    transform: translate(50%, -50%);
    z-index: 1;
  }

  .b-c,
  .d-e {
    border-bottom: 1px solid var(--main-color);
    border-right: 1px solid var(--main-color);
    transform: translate(-50%, -50%);
    z-index: 1;
  }

  .box-a,
  .box-b,
  .box-c,
  .box-d,
  .box-e {
    background-color: var(--text-background-color);
    color: white;
    padding: 1rem;
    border-radius: 0.5rem;
    z-index: 2;
  }
</style>
