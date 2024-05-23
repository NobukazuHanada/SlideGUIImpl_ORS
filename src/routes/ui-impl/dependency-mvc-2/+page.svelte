<script lang="ts">
  import DependencyMVCSlide from '$lib/DependencyMVCSlide.svelte';
  let contllerCode = `const controller = { firstName : "", lastName : "" };
function firstNameOnChange(firstName){
  controller.firstName = firstName;
  setName(firstName, lastName);
}
function lastNameOnChange(lastName){
  controller.lastName = lastName;
  setName(firstName, lastName);
}`;

  let modelCode = `const model = { name : "" };
function setName(firstName, lastName){
  model.name = firstName + " " + lastName;
}`;
  let viewCode = `function draw(){}`;

  let firstName = $state('');
  let lastName = $state('');
</script>

<DependencyMVCSlide
  {contllerCode}
  {modelCode}
  {viewCode}
  modelName={firstName || lastName ? `"${firstName} ${lastName}"` : '""'}
  viewName=""
  bind:firstName
  bind:lastName
>
  <p>Controllerがmodelのメソッドや関数を呼び出して、入力を解釈して、モデル更新をする</p>
</DependencyMVCSlide>
