<script lang="ts">
  import { T } from "@threlte/core";
  import { Collider } from "@threlte/rapier";
  import { DEG2RAD } from "three/src/math/MathUtils";
  import Emitter from "./Emitter.svelte";
  import TestBed from "./TestBed.svelte";
</script>

<T.Group rotation={[0, 45 * DEG2RAD, 0]} position={[0, 1, 0]}>
  <Collider shape={"cuboid"} args={[1, 1, 1]} />
</T.Group>
