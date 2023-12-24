There are 4 properties to transform objects
- position
- scale
- rotation
- quaternion
All classes that inherit from `Object3D` possess the above properties, e.g. `PerspectiveCamera` & `Mesh` 

## transforming objects
```js
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 0xff0000 });
const mesh = new THREE.Mesh(geometry, material);
mesh.position.set(0.7, -0.6, 1); // eqivalent to belo
mesh.position.x = 0.7;
mesh.position.y = -0.6;
mesh.position.z = 1;

// add axes helper to help visualize 
const axesHelper = new THREE.AxesHelper();
scene.add(axesHelper);
// you can also add axesHelper to the object
mesh.add(axesHelper);

//scale
mesh.scale.x = 2;
mesh.scale.y = 0.5;
mesh.scale.z = 0.5;

//rotation 
mesh.rotation.reorder("YXZ");
mesh.rotation.x = Math.PI / 4;
mesh.rotation.y = Math.PI / 4;
// IMPORTANT need to reorder first

//when you change the x,y,z properties imagine putting a stick through the object's center in the axis's direction and then rotating.
//note that when you rotate on one axis, you most likely will roate the other axes as well.
//the default order is XYZ, so an object is first rotated around x then y then z axis.
//change this using object.rotation.reoder('yxz')

//quaternion
//another way to do rotation, just remember when you update an objects rotation, no matter which one you use, rotation or quaternion the other one will be updated.


```
