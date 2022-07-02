#### three入门

三大要素scene，camera，renderer

```
const scene = new THREE.Scene();
//相机角度，相机长宽比，近端面，远端面
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
const renderer = new THREE.WebGLRenderer();
```

