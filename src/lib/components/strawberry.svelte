<script>
  import { Group } from "three";
  import { T, forwardEventHandlers } from "@threlte/core";
  import { useGltf } from "@threlte/extras";

  export const ref = new Group();

  const gltf = useGltf("/assets/strawberry-transformed.glb", { useDraco: true });

  const component = forwardEventHandlers();
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
  {#await gltf}
    <slot name="fallback" />
  {:then gltf}
    <T.Mesh
      geometry={gltf.nodes.strawberry.geometry}
      material={gltf.materials.Strawberry}
      rotation={[-0.05, -1.23, 1.54]}
      scale={1.22}
    />
  {:catch error}
    <slot name="error" {error} />
  {/await}

  <slot {ref} />
</T>
