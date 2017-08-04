<template>
  <div id="app">
  
  </div>
</template>

<script>
import * as THREE from 'three';
// var THREE = require('three');

var scene = new THREE.Scene();//生成场景
var camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );//生成相机

var renderer = new THREE.WebGLRenderer();//生成渲染器
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.style.margin="0px";
document.body.style.overflow="hidden";
renderer.domElement.style.height="100%";
renderer.domElement.style.width="100%";
document.body.appendChild( renderer.domElement );

camera.position.z = 25;//摄像机Z轴距离

var material = new THREE.LineBasicMaterial({ color: 0xffffff });
var geometry = new THREE.Geometry();
geometry.vertices.push(new THREE.Vector3(-25, 0, 0));
// geometry.vertices.push(new THREE.Vector3(0, 10, 0));
geometry.vertices.push(new THREE.Vector3(25, 0, 0));

var geometry1 = new THREE.Geometry();
geometry1.vertices.push(new THREE.Vector3(0, 20, 0));
geometry1.vertices.push(new THREE.Vector3(0, -20, 0));

var line = new THREE.Line(geometry, material);
var line1 = new THREE.Line(geometry1, material);

scene.add(line);
scene.add(line1);

renderer.render(scene, camera);

</script>

<style>
html,body { overflow-y:hidden; }
</style>
