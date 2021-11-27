<script>
import Carousel from "svelte-carousel";
import { onMount } from "svelte";

import expensesData from "./sample1/expenses";
let expenses = [...expensesData];
console.log(expenses);

const apiURL = window.location.href + "/data_en-US.json";
let data = [];

onMount(async function () {
  const response = await fetch(apiURL);
  data = await response.json();
});
</script>

{#key data}
  <Carousel let:loaded autoplay autoplayDuration="{5000}">
    {#each data as item, i}
      <div class="card">
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <img
          class="card-img-top"
          src="{item['LargeImg']}"
          alt="Card image cap" />
        {@html item["svg"]}
        <div class="card-body">
          <h5 class="card-title">{item["Title"]}e</h5>
          <p class="card-text">
            {item["ShortDesc"]}
          </p>
        </div>
      </div>
    {/each}
  </Carousel>
{/key}
