<script>
  import { T } from "@threlte/core";
  import { MeshBasicMaterial, SphereGeometry } from "three";

  export let side = "";

  let x = -0.2;
  if (side === "right") {
    x = 0.2;
  }
</script>

<T.Mesh position={[x, 0, 0]}>
  <T.SphereGeometry args={[0.04, 32, 32]} />
  <T.MeshBasicMaterial color={'#ffccaa'} />
</T.Mesh>
