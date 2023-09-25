<script>
  import { T } from "@threlte/core";
  import { CylinderGeometry, MeshBasicMaterial } from "three";
</script>

<T.Mesh position={[0, -0.1, 0]}>
  <T.CylinderGeometry args={[0.2, 0.2, 0.2, 32]} />
  <T.MeshBasicMaterial color="#808080" />
</T.Mesh>
