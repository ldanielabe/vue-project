
<template>
   <div id="app">
    <div ref="canvas" class="container"> </div>
   </div>
</template>

<script>
import * as THREE from "three"

export default{
  data(){
      const scene = new THREE.Scene();
			const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

			const renderer = new THREE.WebGLRenderer();
			
			const geometry = new THREE.BoxGeometry( 1, 1, 1 );
			const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
			const cube = new THREE.Mesh( geometry, material );
		

    return{
      scene,
      camera,
      renderer,
      geometry,
      material,
      cube
    }
  }, 
  created() {
    this.renderer.setSize( window.innerWidth, window.innerHeight );
		document.body.appendChild( this.renderer.domElement );

	  this.scene.add( this.cube );

		this.camera.position.z = 5;
  },
  mounted() {
    this.animate()
  },
  methods:{
    animate() {
			
      requestAnimationFrame( this.animate );

			this.cube.rotation.x += 0.01;
			this.cube.rotation.y += 0.01;

			this.renderer.render( this.scene, this.camera );
		}
  }
}
</script>


<style>
@import './assets/base.css';

.container {
  width: 100%;
  height: 100vh;
  text-align: center;
}
</style>
