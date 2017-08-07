<template>
	<div id="app">
	
	</div>
</template>

<script>
import * as THREE from 'three';
import Stats from 'stats.js'
export default {
	name: 'app',
	data() {
		return {
		}
	},
	components: {
	}
};
var stats = new Stats();
var scene = new THREE.Scene();
var camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);

var renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
document.body.appendChild(stats.dom);
var geometry = new THREE.BoxGeometry(1, 1, 1);
var material = new THREE.MeshBasicMaterial({ color: 0x00ff66 });
var cube = new THREE.Mesh(geometry, material);
scene.add(cube);

console.log(cube.material);

camera.position.z = 5;

var render = function () {
	requestAnimationFrame(render);

	cube.rotation.x += 0.1;
	cube.rotation.y += 0.1;
	cube.material= new THREE.MeshBasicMaterial({ color: "#"+ InitColor() });
	renderer.render(scene, camera);
	stats.update();
};

render();
function InitColor() {
	var colorStr = "";
	var randomArr = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'];
	for (var i = 0; i < 6; i++) {
		//15是范围上限，0是范围下限，两个函数保证产生出来的随机数是整数  
		colorStr += randomArr[Math.ceil(Math.random() * (15 - 0) + 0)];
	}
	return colorStr;
}


</script>

<style>
body {
	margin: 0px;
	overflow: hidden;
}
</style>
