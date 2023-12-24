```js
// resize
window.addEventListener("resize", (e) => {
	(sizes.width = window.innerWidth), (sizes.height = window.innerHeight);

	// update canvas
	renderer.setSize(sizes.width, sizes.height);

	// update camera
	camera.aspect = sizes.width / sizes.height;
	camera.updateProjectionMatrix();
	
	// in case user drags window to a new screen
	renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
});

// enter & exit fullscreen
window.addEventListener("dblclick", (e) => {
	if (!document.fullscreenElement) canvas.requestFullscreen();
	else document.exitFullscreen();
});

renderer.setSize(sizes.width, sizes.height);
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
```
