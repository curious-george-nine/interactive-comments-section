<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function hideModal() {
    dispatch("hideModal");
  }
</script>

<button
  class="fixed top-0 left-0 w-full h-full bg-black bg-opacity-50 cursor-default flex justify-center items-center"
  on:click={hideModal}
>
  <div
    class="bg-white rounded-xl relative z-10 mx-3 text-left px-8 py-5 lg:w-1/4"
  >
    <h2
      class="text-gray-900 font-bold text-xl pb-5
      "
    >
      Delete comment
    </h2>
    <p class="text-gray-700 pb-5">
      Are you sure you want to delete this comment? This will remove the comment
      and can't be undone.
    </p>
    <div class="grid grid-cols-2 gap-3 text-white">
      <button
        class="bg-gray-500 rounded-lg py-3 uppercase font-bold"
        on:click={hideModal}>no, cancel</button
      >
      <button
        class="bg-rose-400 rounded-lg uppercase font-bold"
        on:click={hideModal}>yes, delete</button
      >
    </div>
  </div></button
>
