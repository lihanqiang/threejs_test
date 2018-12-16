<template lang="pug">
    div.home-wrap
</template>

<script>
import * as THREE from 'three'
export default {
  name: 'home',
  data () {
    return {
      msg: ''
    }
  },
  created() {
    console.log(11)
  },
  mounted() {
    let camera, scene, renderer, geometry, material, mesh

    init()
    animate()
    function init() {
        camera = new THREE.PerspectiveCamera(70, window.innerWidth / window.innerHeight, 0.01, 10)
        camera.position.z = 1
        scene = new THREE.Scene()

        geometry = new THREE.BoxGeometry(0.2, 0.2, 0.2)
        material = new THREE.MeshNormalMaterial()

        mesh = new THREE.Mesh(geometry, material)
        scene.add(mesh)

        renderer = new THREE.WebGLRenderer({ antialias: true })
        renderer.setSize(window.innerWidth, window.innerHeight)
        document.getElementsByClassName('home-wrap')[0].appendChild(renderer.domElement)
    }

    function animate() {
        requestAnimationFrame(animate)

        mesh.rotation.x += 0.01
        mesh.rotation.y += 0.02

        renderer.render(scene, camera)
    }
  }
}
</script>

<style lang="scss" scoped>
.home-wrap{
    width: 100%;
    height: 100%;
    color: red;
}
</style>
