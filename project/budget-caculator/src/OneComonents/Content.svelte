<script>
  import { blur, fade, fly } from "svelte/transition";
</script>

<div class="my-container" in:blur out:fade>
  <div class="my-content" transition:fly={{ y: 200 }}>
    <slot>
      <!-- optional fallback -->
    </slot>
  </div>
</div>
