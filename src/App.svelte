<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm.svelte";

  let showModal = false;

  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "red", age: 33, id: 2 },
    { name: "luigi", beltColor: "green", age: 29, id: 3 },
  ];

  const addPerson = (e) => {
    // console.log(e.detail); //it comes back on e.detail
    // people.push(e.detail); //wont work because svelte looks for reassignment
    const person = e.detail;
    people = [person, ...people]; //you have to totally reassign,
    // also watch for having it the same pointer  people=people.push(person) didnt work
    showModal = false; //will trigger another update cycle?
  };

  const handleClick = ({ id }) => {
    //delete person  from people
    people = people.filter((p) => p.id !== id);
  };

  let num = 5;

  const toggleModal = () => {
    showModal = !showModal;
  };
</script>

<Modal
  message="sign up for offers"
  isPromo={false}
  {showModal}
  on:click={toggleModal}
>
  <AddPersonForm on:addPerson={addPerson} />
</Modal>

{#if num > 20}
  <p>greater than 20</p>
{:else if num > 5}
  <p>num is greater than 5</p>
{:else}
  <p>num is less than 5</p>
{/if}
<main>
  <button on:click|once={toggleModal}>Open Modal</button>
  <!-- even here we can specify once on the onclick event -->
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
