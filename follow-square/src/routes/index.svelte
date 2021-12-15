<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	let width = 1;
	let height = 0.1;
	let depth = 1;

	let spin = 0;

	let spinIncrease = 0.01;

	let boxes = [1,1,2,1,1];

	/*
	SC.onFrame(() => {
		spin += spinIncrease;
		if(spin > 2 && spinIncrease > 0)
		 spinIncrease = -0.01;
		 
		if(spin < 1 && spinIncrease < 0)
		 spinIncrease = 0.01;
	});
	*/
</script>

<SC.Canvas
	antialias
	background={new THREE.Color('papayawhip')}
	fog={new THREE.FogExp2('papayawhip', 0.05)}
	shadows
>
	<SC.Group position={[0, -height / 2, 0]}>
		<SC.Mesh
			geometry={new THREE.PlaneGeometry(50, 50)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[-Math.PI / 2, 0, 0]}
			receiveShadow
		/>  
		<SC.Primitive
			object={new THREE.GridHelper(10, 10, 'papayawhip2', 'papayawhip2')}
			position={[0, 0.001, 0]}
		/>
	</SC.Group>

	<SC.Group 
			rotation={[0, spin, 0]}
			position={[spin, 0.001, 0]}>
		<SC.Mesh
			geometry={new THREE.BoxGeometry()}
			material={new THREE.MeshStandardMaterial({ color: 0xff3e00 })}
			scale={[0.5, 0.5, 0.5]}
			position={[0, 1, 1]}
			castShadow
		/>		
		<SC.Mesh
			geometry={new THREE.BoxGeometry()}
			material={new THREE.MeshStandardMaterial({ color: 0xff3e00 })}
			scale={[1, 0.5, 0.5]}
			position={[0, 0.001, 0]}
			castShadow
		/>
		
{#each boxes as bx}
		<SC.Mesh
			geometry={new THREE.BoxGeometry()}
			material={new THREE.MeshStandardMaterial({ color: 0x3eff00 })}
			scale={[bx, 1, 0.2]}
			position={[0.5, 0.4, bx]}
			castShadow
		/>
	{/each}

	</SC.Group>

	<SC.PerspectiveCamera position={[1, 1, 5]} />
	<SC.OrbitControls enableZoom={true} maxPolarAngle={Math.PI * 0.51} />
	<SC.AmbientLight intensity={0.6} />
	<SC.DirectionalLight intensity={0.6} position={[-2, 3, 2]} shadow={{ mapSize: [2048, 2048] }} />
</SC.Canvas>

<div class="controls">
	<label><input type="range" bind:value={width} min={0.1} max={3} step={0.1} /> width { spin }</label>
	<label><input type="range" bind:value={height} min={0.1} max={3} step={0.1} /> height</label>
	<label><input type="range" bind:value={depth} min={0.1} max={3} step={0.1} /> depth</label>
</div>

<style>
	.controls {
		position: absolute;
		left: 1em;
		top: 1em;
	}

	label {
		display: flex;
		width: 60px;
		gap: 0.5em;
		align-items: center;
	}

	input {
		width: 80px;
		margin: 0;
	}
</style>
