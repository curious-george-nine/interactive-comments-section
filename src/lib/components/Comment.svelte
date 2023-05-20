<script>
  export let score = 0;
  export let isReply = false;
  export let isMine = false;
  export let isLast = false;

  import ActionButtons from "./ActionButtons.svelte";
  import { createEventDispatcher } from "svelte";
  import iconPlus from "$lib/icons/icon-plus.svg";
  import iconMinus from "$lib/icons/icon-minus.svg";

  const dispatch = createEventDispatcher();
</script>

<div
  class="bg-white px-4 py-4 rounded-lg space-y-3 relative {isReply
    ? `ml-3 lg:ml-20 before:absolute before:-left-3 lg:before:-left-10 before:top-0 before:w-0.5 before:bg-gray-200 before:rounded-xl ${
        !isLast ? 'before:h-[125%]' : 'before:h-full'
      }`
    : ''}"
>
  <div class="lg:flex lg:flex-row-reverse lg:gap-5">
    <div>
      <div class="flex gap-5 py-2.5">
        <span>
          <slot name="pfp" />
        </span>
        <span class="text-slate-800 font-semibold">
          <slot name="username" />
          {#if isMine}
            <span class="bg-indigo-500 text-white px-2 text-sm">you</span>
          {/if}
        </span>
        <span>
          <slot name="createdAt" />
        </span>
      </div>
      <div>
        <span>
          <slot name="contents" />
        </span>
      </div>
    </div>
    <div class="mt-3 lg:mt-0">
      <div
        class="rounded-lg bg-blue-500 text-blue-900 font-bold bg-opacity-10 px-4 py-1.5 inline-flex lg:flex-col gap-3 lg:justify-between lg:py-4"
      >
        <button>
          <img src={iconPlus} alt="icon plus" />
        </button>
        <span>{score}</span>
        <button>
          <img src={iconMinus} alt="icon minus" />
        </button>
      </div>
    </div>
    <ActionButtons {isMine} on:deleteClick={() => dispatch("deleteClick")} />
  </div>
</div>
