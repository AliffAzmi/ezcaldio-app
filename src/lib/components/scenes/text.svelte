<script lang="ts">
  import { T, Canvas } from "@threlte/core";
  import { Suspense, Text } from "@threlte/extras";
  import Icon from "@iconify/svelte";

  export let cal;
</script>

<Suspense>
  <Text color="black" text={`${cal.name}`} fontSize={2} anchorX="50%" anchorY="100%" />
  <svelte:fragment slot="fallback">
    <div class="text-center">
      <Icon size={25} icon="line-md:loading-twotone-loop" />
    </div>
  </svelte:fragment>
</Suspense>
