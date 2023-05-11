<script lang="ts">
  import { T } from "@threlte/core";
  import { Vector3, type Color } from "three";
  import { useRigidBody } from "@threlte/rapier";

  export let active_color: Color;

  const rigidBody = useRigidBody();
  const max = 0.06;
  const min = 0.05;
  const forceVector = new Vector3(
    (Math.random() - 0.5) * max,
    Math.random() * max,
    (Math.random() - 0.5) * max
  );
</script>

<T.Mesh
  on:click={() => {
    rigidBody?.applyImpulse(forceVector, true);
  }}
>
  <T.BoxGeometry args={[0.25, 0.25, 0.25]} />
  <T.MeshPhongMaterial color={active_color} transparent={true} opacity={0.3} />
</T.Mesh>
