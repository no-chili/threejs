<template>
  <div class="box"></div>
</template>
<script setup>
// 导入
import {
  Scene,
  PerspectiveCamera,
  WebGLRenderer,
  BoxGeometry,
  MeshBasicMaterial,
  Mesh,
  AxesHelper,
} from "three";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";
import { onMounted } from "vue";
// 场景相机渲染器
const scene = new Scene();
const camera = new PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);
const renderer = new WebGLRenderer();
// 物体
const geometry = new BoxGeometry(1, 1, 1);
// 材质
const material = new MeshBasicMaterial({ color: 0x00ff00 });
// 网格
const cube = new Mesh(geometry, material);
// 轨道控制器
const controls = new OrbitControls(camera, renderer.domElement);
// 辅助线
const axesHelper = new AxesHelper(5);
scene.add(cube);
scene.add(axesHelper);
onMounted(() => {
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.querySelector(".box").appendChild(renderer.domElement);
  camera.position.z = 5;
  function animate() {
    requestAnimationFrame(animate);
    controls.update();
    renderer.render(scene, camera);
  }
  animate();
});
</script>
<style scoped></style>
