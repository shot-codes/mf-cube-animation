<script lang="ts">
  import { Canvas } from "@threlte/core";
  import { HTML } from "@threlte/extras";
  import { World, Debug } from "@threlte/rapier";
  import Scene from "$lib/components/Scene.svelte";
</script>

<div>
  <Canvas>
    <World gravity={[0, -1, 0]}>
      <!-- <Debug depthTest={false} depthWrite={false} /> -->
      <Scene />
      <HTML slot="fallback" transform>
        <p class="text-xs">
          It seems your browser<br />
          doesn't support WASM.<br />
          I'm sorry.
        </p>
      </HTML>
    </World>
  </Canvas>
</div>

<style>
  div {
    width: 100vw;
    height: 100vh;
    background-color: rgb(20, 20, 20);
  }
</style>
