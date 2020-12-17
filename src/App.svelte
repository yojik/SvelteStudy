<script>
	export let name;
	let cameraPos = "0 0 1";
	let pos;
	AFRAME.registerComponent("rotation-reader", {
		schema: { type: "string" },
		tick: function () {
			// カメラ位置を取る
			// `this.el` is the element.
			// `object3D` is the three.js object.

			// `rotation` is a three.js Euler using radians. `quaternion` also available.
			//console.log(this.el.object3D.rotation);

			// `position` is a three.js Vector3.
			//console.log(this.el.object3D.position);
			let p = this.el.object3D.position
			// z軸だけズレたposを生成 本当はちゃんと視点の先にあるように調整する
			pos = p.x + "  " + (p.y ) + " " + (p.z  -3)
  	}
	});
</script>

<style>
	a-scene {
		height: 300px;
		width: 600px;
	}

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1>Hello {name}!</h1>
	<textarea bind:value={cameraPos} />
	<!-- a-frame側から双方向な値を取得する方法を考える-->
	<textarea bind:value={name} />
	{pos}

	<p>
		Visit the
		<a href="https://svelte.dev/tutorial">Svelte tutorial</a>
		to learn how to build Svelte apps.
	</p>

	<a-scene embedded>
		<a-entity
			id="camera"
			position={cameraPos}
			camera
			rotation-reader
			wasd-controls="acceleration:100"
			look-controls>
			<!-- <a-entity
				cursor="fuse: true; fuseTimeout: 500"
				position="0 0 -1"
				
				geometry="primitive: ring; radiusInner: 0.02; radiusOuter: 0.03"
				material="color: black; shader: flat" /> -->
		</a-entity>

		<a-text position="0 0 -1" scale="2 2 2 " color="#ff3e00" value={name} />

		<a-text position="{pos}" scale="2 2 2 " color="blue" value="+" />

	</a-scene>
</main>
