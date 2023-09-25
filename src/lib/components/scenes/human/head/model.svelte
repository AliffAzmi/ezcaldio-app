<script lang="ts">
  import { T } from "@threlte/core";

  import Hair from "./hair.svelte";
  import Eye from "./eye.svelte";
  import Nose from "./nose.svelte";
  import Ear from "./ear.svelte";
  import Mouth from "./mouth.svelte";
</script>

<!-- Head component -->
<T.Mesh position={[0, 1.6, 0]}>
  <!-- Sphere shape -->
  <T.SphereGeometry args={[0.2, 32, 32]} />
  <T.MeshBasicMaterial color={"#ffccaa"} />

  <!-- <Hair /> -->
  <Eye side="left" />
  <Eye side="right" />
  <Nose />
  <Ear side="left" />
  <Ear side="right" />
  <Mouth />
</T.Mesh>
