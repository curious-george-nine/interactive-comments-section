<script>
  export let isMine = false;
  import { createEventDispatcher } from "svelte";
  import ActionButton from "./ActionButton.svelte";
  import iconDelete from "$lib/icons/icon-delete.svg";
  import iconEdit from "$lib/icons/icon-edit.svg";
  import iconReply from "$lib/icons/icon-reply.svg";

  const dispatch = createEventDispatcher();
</script>

<div class="flex gap-4 absolute bottom-4 right-4 lg:top-4">
  {#if isMine}
    <ActionButton icon={iconDelete} on:click={() => dispatch("deleteClick")}>
      <span class="text-rose-400">Delete</span>
    </ActionButton>
    <ActionButton icon={iconEdit}>
      <span class="text-blue-900">Edit</span>
    </ActionButton>
  {:else}
    <ActionButton icon={iconReply}>
      <span class="text-blue-900">Reply</span>
    </ActionButton>
  {/if}
</div>
