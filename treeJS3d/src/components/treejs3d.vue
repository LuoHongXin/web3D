<script setup lang="ts">
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';
var scene, camera, renderer;

function initThree(){
    //场景
    scene = new THREE.Scene();
    //镜头
    camera = new THREE.PerspectiveCamera(90, document.body.clientWidth / document.body.clientHeight, 0.1, 100);
    camera.position.set(0, 0, 0.01);
    //渲染器
    renderer = new THREE.WebGLRenderer();
    renderer.setSize(document.body.clientWidth, document.body.clientHeight);
    document.getElementById("container").appendChild(renderer.domElement);
    //镜头控制器
    var controls = new THREE.OrbitControls(camera, renderer.domElement);
    
    //一会儿在这里添加3D物体

    loop();
}

//帧同步重绘
function loop() {
    requestAnimationFrame(loop);
    renderer.render(scene, camera);
}

window.onload = initThree;
</script>

<template>
  <div id="container"></div>
</template>