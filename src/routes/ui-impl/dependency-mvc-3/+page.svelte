<script lang="ts">
  import DependencyMVCSlide from '$lib/DependencyMVCSlide.svelte';
  let contllerCode = `省略`;

  let modelCode = `const model = { name : "", observer : [] };
function notify(){
    model.observer.forEach(observer => observer());
}
function setName(firstName, lastName){
  model.name = firstName + " " + lastName; notify();
}`;
  let viewCode = `model.observer.push(draw);
function draw(){
    document.querySelector("#name").textContent = model.name;
}`;

  let firstName = $state('');
  let lastName = $state('');
</script>

<DependencyMVCSlide
  {contllerCode}
  {modelCode}
  {viewCode}
  modelName={firstName || lastName ? `"${firstName} ${lastName}"` : '""'}
  viewName={firstName || lastName ? `${firstName} ${lastName}` : ''}
  bind:firstName
  bind:lastName
>
  <p>モデルが、ビューへ通知を送ることで更新する</p>
</DependencyMVCSlide>
