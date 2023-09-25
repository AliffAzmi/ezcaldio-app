<script>
  import { T } from "@threlte/core";
  import { MeshBasicMaterial, SphereGeometry } from "three";
</script>

<T.Mesh position={[0, -0.06, 0.2]}>
  <T.SphereGeometry args={[0.02, 32, 32]} />
  <T.MeshBasicMaterial color={"white"} />
</T.Mesh>
