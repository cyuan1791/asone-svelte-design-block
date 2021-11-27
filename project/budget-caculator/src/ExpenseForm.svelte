<script>
// import { onMount, onDestroy, beforeUpdate, afterUpdate } from "svelte";
// onMount(() => {
//   console.log("form has mounted");
// });
// beforeUpdate(() => {
//   console.count("before update");
// });
// afterUpdate(() => {
//   console.count("after update");
// });
// onDestroy(() => {
//   console.log("form is hidden");
// });
import Title from "./Title.svelte";
export let name = "";
export let amount = null;
export let addExpense;
export let isEditing;
export let editExpense;
export let hideForm;
// $: console.log({ name, amount });

$: isEmpty = !name || !amount;
function handleSubmit() {
  if (isEditing) {
    editExpense({ name, amount });
  } else {
    addExpense({ amount, name });
  }
  name = "";
  amount = null;
  hideForm();
}
</script>

<div class="p-5">
  <div class="d-flex justify-content-around p-4">
    <Title title="add expense" />
    <button type="button" class="close-btn" on:click="{hideForm}">
      <i class="fas fa-times"></i>
      close
    </button>
  </div>
  <hr />
  <form on:submit|preventDefault="{handleSubmit}">
    <div class="form-row">
      <div class="col">
        <label for="name">name</label>
      </div>
      <div class="col">
        <input class="form-control" type="text" id="name" bind:value="{name}" />
      </div>
    </div>
    <div class="form-row">
      <div class="col">
        <label for="amount">amount</label>
      </div>
      <div class="col">
        <input
          type="number"
          class="form-control"
          id="amount"
          bind:value="{amount}" />
      </div>
    </div>
    <div class="form-group">
      {#if isEmpty}
        <p class="form-empty">please fill out all form fields</p>
      {/if}
      <button
        type="submit"
        class="btn btn-primary btn-block"
        class:disabled="{isEmpty}"
        disabled="{isEmpty}">
        {#if isEditing}edit expense{:else}add expense{/if}
      </button>
    </div>
  </form>
</div>
