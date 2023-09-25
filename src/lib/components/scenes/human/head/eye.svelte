<script>
  import { T } from "@threlte/core";
  import { MeshBasicMaterial, SphereGeometry } from "three";

  export let side = "";

  let x = -0.05;
  if (side === "right") {
    x = 0.05;
  }
</script>

<T.Mesh position={[x, 0.04, 0.2]}>
  <T.SphereGeometry args={[0.03, 32, 32]} />
  <T.MeshBasicMaterial color={"#ffffff"} />
</T.Mesh>
