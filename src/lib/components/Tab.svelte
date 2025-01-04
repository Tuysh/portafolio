<script>
  import { createEventDispatcher } from "svelte";

  export let name;
  export let isActive;

  const dispatch = createEventDispatcher();
</script>

<button
  on:click={() => dispatch("click")}
  class={`px-4 py-2 rounded-t text-sm font-mono text-left min-w-[120px] max-w-[200px] relative ${
    isActive
      ? "bg-white text-gray-800"
      : "bg-gray-100 text-gray-600 hover:bg-gray-50"
  }`}
>
  <span class="block truncate">
    {name}
  </span>
  {#if isActive}
    <div class="absolute top-0 left-0 right-0 h-1 bg-white"></div>
  {/if}
</button>
