<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher(); //when we want to emit an event to a parent

  let name;
  let beltColor;
  let age;
  //   let fighting = false;
  //   let sneaking = false;
  //   let running = false;
  let skills = [];

  const handleSubmit = () => {
    const person = { name, beltColor, age, skills, id: Math.random() };
    //console.log(person);
    dispatch("addPerson", person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="text" placeholder="belt color" bind:value={beltColor} />
  <input type="number" placeholder="age" bind:value={age} />
  <label>Skills</label>
  <!-- <input type="checkbox" bind:checked={fighting} />fighting<br />
  <input type="checkbox" bind:checked={sneaking} />sneaking<br />
  <input type="checkbox" bind:checked={running} />running<br /> -->
  <input type="checkbox" bind:group={skills} value="fighting" />fighting<br />
  <input type="checkbox" bind:group={skills} value="sneaking" />sneaking<br />
  <input type="checkbox" bind:group={skills} value="running" />running<br />
  <button>Add person</button>
</form>

<style></style>
