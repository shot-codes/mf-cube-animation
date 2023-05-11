<script lang="ts">
  import { T } from "@threlte/core";
  import { Collider } from "@threlte/rapier";
  import { BoxGeometry, MeshStandardMaterial } from "three";
</script>

<T.Group position={[0, 0.02, 0]}>
  <Collider shape={"cuboid"} args={[100, 0.001, 100]} />
</T.Group>
