<script>
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "red", age: 33, id: 2 },
    { name: "luigi", beltColor: "green", age: 29, id: 3 },
  ];
</script>

<main>
  {#each people as person (person.id)}
    <!-- person.id is the key -->
    <div>
      <h4>{person.name}</h4>
      <p>{person.age} years old, has a {person.beltColor} belt.</p>
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
