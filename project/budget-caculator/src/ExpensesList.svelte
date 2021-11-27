<script>
  import SectionTitle from "./Title.svelte";
  import Expense from "./Expense.svelte";
  import { fly } from "svelte/transition";
  import { flip } from "svelte/animate";
  export let expenses = [];
</script>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>

<section>
  <SectionTitle title="expense list" />
  <ul class="list-group">
    {#each expenses as expense, index (expense.id)}
      <li class="list-group-item"
        in:fly={{ x: 200, delay: (index + 1) * 700 }}
        out:fly={{ x: -200 }}
        animate:flip>
        <Expense {...expense} />
  </li>
    {:else}
      <h2>no expenses added to the list</h2>
    {/each}
  </ul>
</section>
