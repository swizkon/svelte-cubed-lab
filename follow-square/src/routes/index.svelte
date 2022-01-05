<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';
	
	import Bike from '../components/bike/Bike.svelte';

	import { of } from "rxjs";
  import { delay, startWith } from "rxjs/operators";

  // emit an array with initial delay of 2s
  const values = of([1, 2, 3, 4, 5]).pipe(
    delay(2000),
    startWith([])
  );

	let width = 1;
	let height = 0.1;
	let depth = 1;

	let spin = 0;


	let bikes = [[0, 0, 0],[10, 0, 2]];

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
	fog={new THREE.FogExp2('papayawhip', 0.01)}
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
			object={new THREE.GridHelper(50, 30, 'papayawhip2', 'papayawhip2')}
			position={[0, 0.001, 0]}
		/>
	</SC.Group>

	
{#each $values as v}
<Bike position={[0, 0, v]} />
{/each}

	<Bike position={[0, 0, 0]} />
	
	<Bike position={[10, 0, 2]} />

	<SC.PerspectiveCamera position={[10, 5, 10]} />
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
