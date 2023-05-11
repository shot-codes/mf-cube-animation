<script lang="ts">
  import { T } from "@threlte/core";
  // import { OrbitControls } from "@threlte/extras";
  import { onMount } from "svelte";
  import Emitter from "./Emitter.svelte";
  import TestBed from "./TestBed.svelte";
  import Wall from "./Wall.svelte";

  let canvas_w = 1;
  let canvas_h = 1;
  let aspect = 1;
  const frustumSize = 4;

  onMount(() => {
    canvas_w = window.innerWidth;
    canvas_h = window.innerHeight;
    aspect = canvas_w / canvas_h;
  });
</script>

<T.OrthographicCamera
  makeDefault
  manual
  args={[(frustumSize * aspect) / -2, (frustumSize * aspect) / 2, frustumSize, 0, 1, 1000]}
/>

<!-- <T.PerspectiveCamera
  on:create={({ ref }) => {
    ref.lookAt(0, 0, -5)
  }}
  position.x={5}
  position.z={5}
  position.y={5}
  fov={40}
  makeDefault
>
  <OrbitControls target={[0,0,-5]}/>
</T.PerspectiveCamera> -->

<T.DirectionalLight castShadow position={[-8, 20, 3]} />

<T.AmbientLight intensity={0.2} />

<T.Group position.z={-5}>
  <Emitter />
  <TestBed />
  <Wall x_pos={0.35} x_rot={0.1} />
  <Wall x_pos={-0.35} x_rot={-0.1} />
</T.Group>
