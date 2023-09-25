<script lang="ts">
  import { T, Canvas } from "@threlte/core";
  import { GLTF, OrbitControls } from "@threlte/extras";

  import calculators from "$lib/data/calculators";
  // import TextScene from "$lib/components/scenes/text.svelte";
</script>

{#each calculators as cal (cal.id)}
  <div
    id={`anchor-${cal.path}`}
    class="flex flex-col justify-center items-center h-screen border-y border-black snap-center"
  >
    <div class="px-6 text-center">
      <h4 class=" text-2xl font-bold mt-10">{cal.name}</h4>
      <p class="py-4">
        In publishing and graphic design, Lorem ipsum is a placeholder text commonly used to demonstrate the visual form
        of a document or a typeface without relying on meaningful content. Lorem ipsum may be used as a placeholder
        before final copy is available.
      </p>
      <a class=" btn btn-blue" href={`/${cal.path}`} alt={cal.name}>Calculate</a>
    </div>
  </div>
{/each}

<style>
  .btn {
    @apply font-bold py-2 px-4 rounded-md shadow-lg;
  }
  .btn-blue {
    @apply bg-blue-500 text-white;
  }
  .btn-blue:hover {
    @apply bg-blue-700;
  }
</style>
