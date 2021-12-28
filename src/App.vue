<script setup lang="ts">
import { onMounted } from '@vue/runtime-core';
import { ArcRotateCamera, Engine, Scene, Vector3 } from 'babylonjs';

onMounted(() => {
  const canvas = document.querySelector<HTMLCanvasElement>('#container');
  const engine = new Engine(canvas);
  const scene = createScene(engine);
  engine.runRenderLoop(() => {
    scene.render();    
  });
});

const createScene = (engine: Engine) => {
  const scene = new Scene(engine);
  const camera = new ArcRotateCamera('camera', 0, 0, 10, Vector3.Zero(), scene);
  return scene;
};

</script>

<template>
  <canvas id="container" ></canvas>
</template>

<style>
html,
body,
#app,
#container {
  margin: 0;
  width: 100%;
  height: 100%;
}
</style>
