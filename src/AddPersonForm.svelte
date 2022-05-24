<script>
  let name;
  let beltColor;
  let age;
  //   let fighting = false;
  //   let sneaking = false;
  //   let running = false;
  let skills = [];

  const handleSubmit = () => {
    console.log(`name ${name}, color ${beltColor}, age ${age}`);
    console.log(skills);
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
