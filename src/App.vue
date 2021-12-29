<script setup lang="ts">
import { onMounted } from '@vue/runtime-core';
import { ArcRotateCamera, Color3, Engine, MeshBuilder, Scene, Vector3, Color4, DirectionalLight } from 'babylonjs';

onMounted(() => {
  const canvas = document.querySelector<HTMLCanvasElement>('#container');
  const engine = new Engine(canvas);
  const scene = createScene(engine);
  engine.runRenderLoop(() => {
    scene.render();    
  });
});

const createScene = (engine: Engine) => {
  /** 创建场景 */
  const scene = new Scene(engine);
  scene.clearColor = Color4.FromColor3(Color3.Gray());
  /** end */

  /** 创建相机 */
  const camera = new ArcRotateCamera('camera', 0, 0, 10, Vector3.Zero(), scene);
  camera.attachControl(true);
  /** end */

  /** 创建立方体 */
  const box = MeshBuilder.CreateBox('box', { width: 2, height: 3, depth: 4 }, scene);
  /** end */

  /** 创建灯光 */
  const light = new DirectionalLight('light', Vector3.Down(), scene);
  light.diffuse = Color3.Red();
  light.specular = Color3.Green();
  /** end */

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
