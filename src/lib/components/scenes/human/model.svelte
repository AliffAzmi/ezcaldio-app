<script lang="ts">
  import { T } from "@threlte/core";
  import { ContactShadows, OrbitControls } from "@threlte/extras";

  import Head from "$lib/components/scenes/human/head/model.svelte";
  import Torso from "$lib/components/scenes/human/Torso.svelte";
  import FemaleTorso from "$lib/components/scenes/human/FemaleTorso.svelte";
  import Arm from "$lib/components/scenes/human/Arm.svelte";
  import Hand from "$lib/components/scenes/human/Hand.svelte";
  import Waist from "$lib/components/scenes/human/Waist.svelte";
  import Leg from "$lib/components/scenes/human/Leg.svelte";
  import Foot from "$lib/components/scenes/human/Foot.svelte";
</script>

<T.PerspectiveCamera makeDefault position={[10, 5, 15]}>
  <!-- fov={70} -->
  <OrbitControls enableZoom={false} enablePan={false} enableDamping />
  <!-- autoRotate autoRotateSpeed={2.0} -->
</T.PerspectiveCamera>

<T.Mesh scale={4}>
  <T.Group>
    <Head />
    <!-- <Torso /> -->
    <FemaleTorso />
    <Arm side="left" />
    <Arm side="right" />
    <Hand side="left" />
    <Hand side="right" />
    <Leg side="left" />
    <Leg side="right" />
    <Foot side="left" />
    <Foot side="right" />
    <!-- <Waist /> -->
  </T.Group>
</T.Mesh>
