<script>
  import { T } from "@threlte/core";
  import { ContactShadows, OrbitControls } from "@threlte/extras";

  // const strawberry_component = import("$lib/components/strawberry.svelte").then(({ default: C }) => C);
  const scale_component = import("$lib/components/scenes/scale_we.svelte").then(({ default: C }) => C);

  // import { spring } from "svelte/motion";
  // import Box from "$lib/components/Box.svelte";
  // const { target } = interactivity();
  // target.set(document.getElementById("int-target") ?? undefined);
  // const pos = spring({ x: 0, z: 0 });
  // const setRandomPos = () => {
  //   pos.set({
  //     x: Math.random() * 10 - 5,
  //     z: Math.random() * 10 - 5,
  //   });
  // };
</script>

<T.PerspectiveCamera makeDefault position={[5, 10, 13]} fov={12}>
  <OrbitControls enableZoom={false} enablePan={false} enableDamping autoRotate autoRotateSpeed={2.0} />
</T.PerspectiveCamera>

<T.DirectionalLight intensity={0.8} position={[1, 2, 1]} />

<T.AmbientLight intensity={0.2} />

<!-- <Grid
  position.y={-0.001}
  cellColor="#ffffff"
  sectionColor="#ffffff"
  sectionThickness={0}
  fadeDistance={25}
  cellSize={2}
/> -->

<!-- <Float
  floatIntensity={1}
  floatingRange={[0, 1]}
> -->
<!-- position.y={0.5} -->
<!-- position.z={1.5} -->
<!-- <T.Mesh> -->
<!-- <T.BoxGeometry /> -->
<!-- <T.MeshStandardMaterial color="lightGrey" /> -->
<!-- <GLTF castShadow receiveShadow interactive scale={1} url={"assets/digital_weight_scale/scene.gltf"} /> -->
<!-- </T.Mesh> -->
<!-- <GLTF castShadow receiveShadow interactive scale={1} url={"assets/digital_weight_scale/scene.gltf"} /> -->
<T.Mesh>
  {#await scale_component}
    Loading...
  {:then Component}
    <Component />
  {/await}
  <ContactShadows scale={10} blur={2} far={5} opacity={0.2} />
</T.Mesh>

<!-- </Float> -->

<!-- <Box on:click={setRandomPos} position.x={$pos.x} position.z={$pos.z} /> -->
