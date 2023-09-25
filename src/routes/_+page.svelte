<script lang="ts">
  import { T, Canvas } from "@threlte/core";

  import Human from "$lib/components/scenes/human/model.svelte";
</script>

<div class="flex h-screen">
  <div class="w-100 h-full m-auto">
    <Canvas>
      <Human />
    </Canvas>
  </div>
</div>
