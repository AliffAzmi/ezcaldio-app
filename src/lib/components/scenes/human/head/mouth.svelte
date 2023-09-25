<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
</script>

<T.Mesh position={[0, -0.14, 0.15]}>
  <T.BoxGeometry args={[0.1, 0.02, 0.02]} />
  <T.MeshBasicMaterial color={"#ff0000"} />
</T.Mesh>
