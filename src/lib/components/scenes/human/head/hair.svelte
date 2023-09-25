<script>
  import { T } from "@threlte/core";
  import { BoxGeometry, MeshBasicMaterial } from "three";
</script>

<!-- <T.Mesh position={[0, 0.22, 0]}>
  <T.BoxGeometry args={[0.25, 0.2, 0.2]} />
  <T.MeshBasicMaterial color={"#000000"} />
</T.Mesh> -->

<T.Group>
  <!-- Create multiple hair strands using BoxGeometry -->

  <!-- Top of the head: Darker hair color -->
  <T.Mesh position={[0, 0.21, 0]} rotation={[0, 0, Math.PI / 16]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#000000"} />
  </T.Mesh>
  <T.Mesh position={[0, 0.21, 0]} rotation={[0, 0, -Math.PI / 16]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#000000"} />
  </T.Mesh>

  <!-- <T.Mesh position={[0.08, 0.22, 0]} rotation={[0, 0, Math.PI / 16]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#333333"} />
  </T.Mesh>

  <T.Mesh position={[-0.08, 0.22, 0]} rotation={[0, 0, -Math.PI / 16]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#666666"} />
  </T.Mesh>

  <T.Mesh position={[0.16, 0.22, 0]} rotation={[0, 0, Math.PI / 12]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#444444"} />
  </T.Mesh>

  <T.Mesh position={[-0.16, 0.22, 0]} rotation={[0, 0, -Math.PI / 12]}>
    <T.BoxGeometry args={[0.25, 0.02, 0.02]} />
    <T.MeshBasicMaterial color={"#555555"} />
  </T.Mesh> -->
</T.Group>
