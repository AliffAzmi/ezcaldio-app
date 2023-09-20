<script>
  import { Group } from 'three'
  import { T, forwardEventHandlers } from '@threlte/core'
  import { useGltf } from '@threlte/extras'

  export const ref = new Group()

  const gltf = useGltf('/assets/scale.glb', { useDraco: true })

  const component = forwardEventHandlers()
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
  {#await gltf}
    <slot name="fallback" />
  {:then gltf}
    <T.Group rotation={[-Math.PI / 2, 0, 0]}>
      <T.Mesh geometry={gltf.nodes.Object_2.geometry} material={gltf.materials.Green} />
      <T.Mesh geometry={gltf.nodes.Object_3.geometry} material={gltf.materials.Black} />
      <T.Mesh geometry={gltf.nodes.Object_4.geometry} material={gltf.materials.Glass} />
      <T.Mesh geometry={gltf.nodes.Object_5.geometry} material={gltf.materials.Metal} />
    </T.Group>
  {:catch error}
    <slot name="error" {error} />
  {/await}

  <slot {ref} />
</T>
