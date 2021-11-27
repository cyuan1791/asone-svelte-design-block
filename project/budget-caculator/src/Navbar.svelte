<script>
export let showForm;
</script>

<nav class="navbar navbar-light bg-light justify-content-around">
  <h1 class="text-center">budget calculator</h1>
  <button type="button" class="btn btn-primary" on:click="{showForm}">
    <i class="far fa-plus-square"></i>
    add item
  </button>
</nav>
