<script lang="ts">
  import { T } from "@threlte/core";
  import { Collider } from "@threlte/rapier";
  import { BoxGeometry, MeshStandardMaterial } from "three";

  export let x_pos: number;
</script>

<T.Group position={[0, 0.02, x_pos]}>
  <Collider shape={"cuboid"} args={[10, 100, 0.1]} />
</T.Group>
