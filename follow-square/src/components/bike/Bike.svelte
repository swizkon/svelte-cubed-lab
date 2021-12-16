<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';
	import BikeWheel from './BikeWheel.svelte';

	export let position = [0, 0.6, 0];
</script>

<SC.Group scale={[0.5, 0.5, 0.5]} position={position}>
	<SC.Mesh
		geometry={new THREE.BoxGeometry(50, 5, 10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		scale={[0.1, 0.1, 0.1]}
		position={[4, 0.3, 0]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(3, 50, 5)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		scale={[0.1, 0.1, 0.1]}
		position={[1.6, 2.6, 0]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(3, 3, 30)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		scale={[0.1, 0.1, 0.1]}
		position={[1.6, 5, 0]}
		castShadow
	/>
	<!-- 	
	<SC.Mesh
		geometry={new THREE.TorusGeometry(10, 5, 50, 40, 7)}
		material={new THREE.MeshStandardMaterial({ color: 0x00ff33 })}
		scale={[0.1, 0.1, 0.1]}
		rotation={[0, 0, 0]}
	
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.TorusGeometry(10, 5, 5, 40, 7)}
		material={new THREE.MeshStandardMaterial({ color: 0x00ff33 })}
		scale={[0.1, 0.1, 0.1]}
		rotation={[0, 0, 0]}
		position={[0, 0, 0]}
		castShadow
	/> -->

	<BikeWheel position={[8, 0, 0]} />

	<BikeWheel position={[0, 0, 0]} />
</SC.Group>
