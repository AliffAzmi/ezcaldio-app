<script>
  import { T } from "@threlte/core";
  import { SphereGeometry, MeshBasicMaterial } from "three";
  export let side = "";

  let x = -0.26;
  if (side === "right") {
    x = 0.26;
  }
</script>

<T.Mesh position={[x, 0.95, 0]}>
  <T.SphereGeometry args={[0.07, 32, 32]} />
  <T.MeshBasicMaterial color={"#ffccaa"} />
</T.Mesh>
