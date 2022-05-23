<script>
  import Modal from "./Modal.svelte";

  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "red", age: 33, id: 2 },
    { name: "luigi", beltColor: "green", age: 29, id: 3 },
  ];

  const handleClick = ({ id }) => {
    //delete person  from people
    people = people.filter((p) => p.id !== id);
  };

  let num = 5;
</script>

<Modal />

{#if num > 20}
  <p>greater than 20</p>
{:else if num > 5}
  <p>num is greater than 5</p>
{:else}
  <p>num is less than 5</p>
{/if}
<main>
  {#each people as person (person.id)}
    <!-- person.id is the key -->
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === "black"}
        <p><strong>Master Ninja</strong></p>{/if}
      <p>{person.age} years old, has a {person.beltColor} belt.</p>
      <button on:click={() => handleClick(person)}>delete</button>
    </div>
  {:else}
    <p>there are no people to show</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
