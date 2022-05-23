<script>
  let showModal = true;
  let isPromo = false;
</script>

{#if showModal}
  <div class="backdrop">
    <div class="modal" class:promo={isPromo}><p>sign up for offers</p></div>
    <!-- the class: adds classes conditionally -->
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background-color: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background-color: white;
  }

  .promo.modal {
    background-color: crimson;
    color: white;
  }
</style>
