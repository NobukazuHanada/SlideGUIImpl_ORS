<script lang="ts">
  import DependencyMVCSlide from '$lib/DependencyMVCSlide.svelte';
  let contllerCode = `function firstNameOnChange(firstName){}
function lastNameOnChange(lastName){}`;

  let modelCode = `const model = { name : "" };
function setName(firstName, lastName){
  model.name = firstName + " " + lastName;
}`;
  let viewCode = `function draw(){}`;
</script>

<DependencyMVCSlide
  {contllerCode}
  {modelCode}
  {viewCode}
  modelName={'""'}
  viewName={''}
  firstName=""
  lastName=""
>
  <p>
    Dependency MVCについて解説 Model View
    Contllerの関係がまだありませんが、Modelの更新処理がすでにあります
  </p>
</DependencyMVCSlide>
