<!-- FemaleTorso.svelte -->
<script>
  import { T } from "@threlte/core";
</script>

<T.Group>
  <T.Mesh position={[0, 1.1, 0]}>
    <T.BoxGeometry args={[0.4, 0.6, 0.2]} />
    <T.MeshBasicMaterial color={"#f0c8c8"} />
    <!-- Skin color or texture -->
  </T.Mesh>

  <!-- <T.Group>
    <T.Mesh position={[-0.1, 0.45, 0.05]}>
      <T.SphereGeometry args={[0.12, 32, 32]} />
      <T.MeshBasicMaterial color={"#f0c8c8"} />
    </T.Mesh>

    <T.Mesh position={[0.1, 0.45, 0.05]}>
      <T.SphereGeometry args={[0.12, 32, 32]} />
      <T.MeshBasicMaterial color={"#f0c8c8"} />
    </T.Mesh>
  </T.Group> -->

  <!-- Navel -->

  <!-- <T.Mesh position={[0, 0.2, 0.1]}>
    <T.SphereGeometry args={[0.02, 32, 32]} />
    <T.MeshBasicMaterial color={"#000"} />
  </T.Mesh> -->

  <!-- Add more details and refinements as needed -->
</T.Group>
