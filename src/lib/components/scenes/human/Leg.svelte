<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
  export let side = "";

  let x = -0.15;
  if (side === "right") {
    x = 0.15;
  }
</script>

<T.Mesh position={[x, 0.6, 0]}>
  <T.BoxGeometry args={[0.1, 0.4, 0.1]} />
  <T.MeshBasicMaterial color={"darkblue"} />
</T.Mesh>
