<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
  export let side = "";

  let x = -0.15;
  if (side === "right") {
    x = 0.15;
  }
</script>

<T.Mesh position={[x, 0.32, 0]}>
  <T.BoxGeometry args={[0.15, 0.1, 0.2]} />
  <T.MeshBasicMaterial color={0x000000} />
</T.Mesh>
