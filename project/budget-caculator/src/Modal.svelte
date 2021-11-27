<script>
import { blur, fade, fly } from "svelte/transition";
export let modalID;
</script>

<!-- <div class="modal-container" in:blur out:fade>
  <div class="modal-content" transition:fly={{ y: 200 }}>
    <slot>
    </slot>
  </div>
</div> -->

<div
  class="modal fade"
  id="{modalID}"
  tabindex="-1"
  role="dialog"
  aria-labelledby="exampleModalLabel"
  aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <!-- <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div> -->
      <div class="modal-body">
        <slot />
      </div>
      <div class="modal-footer"></div>
    </div>
  </div>
</div>
