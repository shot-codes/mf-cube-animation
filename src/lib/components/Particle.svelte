<script lang="ts" context="module">
  let h = 0.125;
  const points = [
    new Vector3(-h, -h, h),
    new Vector3(h, -h, h),
    new Vector3(h, h, h),
    new Vector3(-h, h, h),
    new Vector3(-h, -h, h),

    new Vector3(-h, -h, -h),
    new Vector3(h, -h, -h),
    new Vector3(h, h, -h),
    new Vector3(-h, h, -h),
    new Vector3(-h, -h, -h),

    new Vector3(-h, -h, h),
    new Vector3(-h, h, h),
    new Vector3(-h, h, -h),

    new Vector3(h, h, -h),
    new Vector3(h, h, h),
    new Vector3(h, -h, h),
    new Vector3(h, -h, -h),
  ];
  const geometry = new BufferGeometry().setFromPoints(points);
</script>

<script lang="ts">
  import { T } from "@threlte/core";
  import { Collider, RigidBody } from "@threlte/rapier";
  import { type Euler, Color, BufferGeometry, Vector3 } from "three";
  import ShadowParticle from "./ShadowParticle.svelte";

  let white = new Color(0xffffff);
  let green = new Color(0x00ff00);
  let active_color = white;

  export let position: Parameters<Vector3["set"]>;
  export let rotation: Parameters<Euler["set"]>;
</script>

<T.Group {position} {rotation}>
  <RigidBody
    type={"dynamic"}
    on:wake={() => {
      active_color = green;
    }}
    on:sleep={() => {
      active_color = white;
    }}
  >
    <Collider shape={"cuboid"} restitution={1} args={[0.125, 0.125, 0.125]} />
    <T.Line {geometry}>
      <T.LineBasicMaterial color={active_color} />
    </T.Line>
    <ShadowParticle {active_color} />
  </RigidBody>
</T.Group>
