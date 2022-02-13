<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	export let position = [0, 0, 0];
</script>

<SC.Group position={position}>
	<SC.Mesh
		geometry={new THREE.BoxGeometry(200, 30, 160)}
		material={new THREE.MeshStandardMaterial({ color: 0x336699 })}
		scale={[1,1,1]}
		position={[0, 20, 0]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(10, 15, 10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		position={[-95, -2.5, -75]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(10, 15, 10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		position={[-95, -2.5, 75]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(10, 15, 10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		position={[95, -2.5, 75]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.BoxGeometry(10, 15, 10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		position={[95, -2.5, -75]}
		castShadow
	/>
	
</SC.Group>
