<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
</script>

<T.Mesh position={[0, 1.1, 0]}>
  <T.BoxGeometry args={[0.4, 0.6, 0.2]} />
  <T.MeshBasicMaterial color={"#808080"} />
</T.Mesh>
