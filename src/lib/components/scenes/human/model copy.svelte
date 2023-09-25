<script>
  import { T } from "@threlte/core";
  import { ContactShadows, OrbitControls } from "@threlte/extras";
  import { BoxGeometry, CylinderGeometry, MeshBasicMaterial, SphereGeometry } from "three";

  import HumanHead from "$lib/components/scenes/human/Head.svelte";
</script>

<!-- <PerspectiveCamera fov={75} aspect={window.innerWidth / window.innerHeight} near={0.1} far={1000} position={[0, 0, 2]} /> -->
<T.PerspectiveCamera makeDefault position={[5, 10, 13]} fov={50}>
  <OrbitControls enableZoom={false} enablePan={false} enableDamping autoRotate autoRotateSpeed={2.0} />
</T.PerspectiveCamera>

<T.Group>
  <!-- Body -->
  <!-- <T.MeshBasicMaterial color={"#808080"} /> -->

  <!-- Head -->
  <T.Mesh position={[0, 0.5, 0]}>
    <T.SphereGeometry position={[0.2, 32, 32]} />
    <T.MeshBasicMaterial color={"#808080"} />
  </T.Mesh>

  <!-- Left Arm -->
  <T.Mesh position={[1, 0.2, 0]}>
    <T.BoxGeometry args={[0.5, 0.2, 0.5]} />
    <T.MeshBasicMaterial color="#808080" />
  </T.Mesh>

  <!-- Right Arm -->
  <T.Mesh position={[-1, 0.2, 0]}>
    <T.BoxGeometry args={[0.1, 0.3, 0.1]} />
    <T.MeshBasicMaterial color="#808080" />
  </T.Mesh>

  <!-- Waist -->
  <T.Mesh position={[0, -0.1, 0]}>
    <T.CylinderGeometry position={[0.15, 0.15, 0.1, 32]} />
    <T.MeshBasicMaterial color={"#555555"} />
  </T.Mesh>

  <!-- Left Leg -->
  <T.Mesh position={[-0.15, -0.7, 0]}>
    <T.BoxGeometry args={[0.1, 0.4, 0.1]} />
    <T.MeshBasicMaterial color="#808080" />
  </T.Mesh>

  <!-- Right Leg -->
  <T.Mesh position={[0.15, -0.7, 0]}>
    <T.BoxGeometry args={[0.1, 0.4, 0.1]} />
    <T.MeshBasicMaterial color="#808080" />
  </T.Mesh>
</T.Group>
