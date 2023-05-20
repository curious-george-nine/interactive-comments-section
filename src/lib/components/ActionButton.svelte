<script>
  export let icon = "";

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
</script>

<div class="font-bold">
  <button class="flex items-center gap-1" on:click={() => dispatch("click")}>
    <img src={icon} alt="reply icon" class="relative top-1" />
    <slot />
  </button>
</div>
