<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
  export let side = "";

  let x = -0.25;
  if (side === "right") {
    x = 0.25;
  }
</script>

<T.Mesh position={[x, 1.20, 0]}>
  <T.BoxGeometry args={[0.1, 0.4, 0.1]} />
  <T.MeshBasicMaterial color={"#ffccaa"} />
</T.Mesh>
