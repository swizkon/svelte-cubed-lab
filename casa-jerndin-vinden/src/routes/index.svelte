<script>
	import { onMount } from 'svelte';
	import { browser } from '$app/env';
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	import Bed from '../components/Bed.svelte';
	import Stairs from '../components/Stairs.svelte';

	onMount(async () => {
		// await start();
	});

	let width = 1;
	let height = 0.1;
	let depth = 1;
	
	let bedPos = [-200, 1, 100];
</script>

<SC.Canvas
	antialias
	background={new THREE.Color('papayawhip')}
	fog={new THREE.FogExp2('papayawhip', 0.005)}
	shadows
>
	<SC.Group scale={[0.1,0.1,0.1]} position={[0, -height / 2, 0]}>
		
		<SC.Mesh
			geometry={new THREE.PlaneGeometry(800, 500)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[-Math.PI / 2, 0, 0]}
			position={[50, 0, 0]}
			receiveShadow
		/>
		<SC.Mesh
			geometry={new THREE.PlaneGeometry(400, 150)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[-Math.PI / 2, 0, 0]}
			position={[250, 0, 320]}
			receiveShadow
		/>
		
		
		<SC.Mesh
			geometry={new THREE.PlaneGeometry(800, 500)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[Math.PI / 3, 0, 0]}
			position={[0, 100, -100]}
			receiveShadow
		/>

		<SC.Mesh
			geometry={new THREE.PlaneGeometry(800, 450)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[-Math.PI, 0, 0]}
			position={[50, 0, 400]}
			receiveShadow
		/>
		
		<SC.Mesh
			geometry={new THREE.PlaneGeometry(800, 450)}
			material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
			rotation={[0, -Math.PI / 2, 0]}
			position={[500, 0, 0]}
			receiveShadow
		/>

		<SC.Primitive
			object={new THREE.GridHelper(700, 50, 'papayawhip2', 'papayawhip2')}
			position={[0, 0.001, 0]}
		/>
	
		<Stairs position={[60, -15, 0]} />
		<Bed position={bedPos} />
	</SC.Group>

	<SC.PerspectiveCamera position={[-40, 80, 80]} />
	<SC.OrbitControls enableZoom={true} maxPolarAngle={Math.PI * 0.51} />
	<SC.AmbientLight intensity={0.6} />
	<SC.DirectionalLight
		intensity={0.6}
		position={[-2, 3, 2]}
		shadow={{ mapSize: [2048, 2048] }}
	/>
</SC.Canvas>

<div class="controls">
	<label
		><input type="range" bind:value={width} min={0.1} max={3} step={0.1} /> width</label
	>
	<label
		><input type="range" bind:value={height} min={0.1} max={3} step={0.1} /> height</label
	>
	<label
		><input type="range" bind:value={depth} min={0.1} max={3} step={0.1} /> depth</label
	>
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
