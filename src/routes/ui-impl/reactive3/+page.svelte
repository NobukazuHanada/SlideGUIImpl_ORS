<script lang="ts">
  import Slide from '$lib/Slide.svelte';

  const code: string = `c = a + b;
if( c < d ){
    e = c;
}else{
    e = d;
}`;

  let a = $state(0);
  let b = $state(0);
  let c = $derived(a + b);
  let d = $state(0);
  let e = $derived.by(() => {
    if (c < d) {
      return c;
    } else {
      return d;
    }
  });
  let acActive = $state(false);
  let bcActive = $state(false);
  let ceActive = $state(false);
  let deActive = $state(false);
  let eOutActive = $state(false);
  $inspect(a).with((type, _) => {
    console.log(type);
    if (type === 'update') {
      acActive = true;
      setTimeout(() => {
        acActive = false;
      }, 100);
    }
  });
  $inspect(b).with((type, _) => {
    if (type === 'update') {
      bcActive = true;
      setTimeout(() => {
        bcActive = false;
      }, 100);
    }
  });
  $inspect(c).with((type, _) => {
    if (type === 'update') {
      ceActive = true;
      setTimeout(() => {
        ceActive = false;
      }, 100);
    }
  });
  $inspect(d).with((type, _) => {
    if (type === 'update') {
      deActive = true;
      setTimeout(() => {
        deActive = false;
      }, 100);
    }
  });
  $inspect(e).with((type, _) => {
    if (type === 'update') {
      eOutActive = true;
      setTimeout(() => {
        eOutActive = false;
      }, 100);
    }
  });
</script>

<Slide>
  <h1>Reactive Programming3</h1>
  <p>入力の変化の伝搬を見てみよう</p>
  <div class="code-and-visual">
    <pre><code>{code}</code></pre>
    <div class="visual">
      <p class="box-a">a = <input type="number" bind:value={a} /></p>
      <p class="box-b">b = <input type="number" bind:value={b} /></p>
      <p class="box-c">c = {c}</p>
      <p class="box-d">d = <input type="number" bind:value={d} /></p>
      <p class="box-e">e = {e}</p>
      <div class="a-c" class:active={acActive}></div>
      <div class="b-c" class:active={bcActive}></div>
      <div class="c-e" class:active={ceActive}></div>
      <div class="d-e" class:active={deActive}></div>
      <div class="e-out" class:active={eOutActive}></div>
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
      'blank1 blank7 c-e box-e d-e blank8'
      'blank1 blank9 c-e e-out blank10 blank8';
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

  .e-out {
    grid-area: e-out;
    border-left: 1px solid var(--main-color);
    transform: translate(50%, 0);
    z-index: 1;
    height: 2rem;
  }

  @keyframes active-animation {
    0% {
      border-color: var(--main-color);
    }

    50% {
      border-color: var(--accent-color);
    }

    100% {
      border-color: var(--main-color);
    }
  }

  .a-c.active,
  .b-c.active,
  .c-e.active,
  .d-e.active,
  .e-out.active {
    animation: active-animation 0.3s ease 0s;
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

  input {
    width: 4rem;
  }
</style>
