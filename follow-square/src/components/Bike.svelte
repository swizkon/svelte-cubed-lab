<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';
	import { RingGeometry } from 'three';

	let width = 1;
	let height = 0.1;
	let depth = 1;

	let spin = 0;
</script>

<SC.Group
scale={[0.5, 0.5, 0.5]}
 position={[0, 0.6, 0]}>
	<SC.Mesh
		geometry={new THREE.BoxGeometry()}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		scale={[0.5, 0.5, 0.5]}
		position={[0, 1, 1]}
		castShadow
	/>
	<SC.Mesh
		geometry={new THREE.BoxGeometry(50, 8,10)}
		material={new THREE.MeshStandardMaterial({ color: 0x003eff })}
		scale={[0.1, 0.1, 0.1]}
		position={[3, 0.3, 0]}
		castShadow
	/>
<!-- 	
	<SC.Mesh
		geometry={new THREE.CylinderGeometry(10, 10, 5, 50, 1)}
		material={new THREE.MeshStandardMaterial({ color: 0xffff00  })}
		scale={[0.1, 0.1, 0.1]}
		rotation={[1.5, 0, 0]}
		position={[2, 1, 2]}
		castShadow
	/> -->
	
	<SC.Mesh
		geometry={new THREE.TorusGeometry(10, 5, 50, 40, 7)}
		material={new THREE.MeshStandardMaterial({ color: 0x00ff33 })}
		scale={[0.1, 0.1, 0.1]}
		rotation={[0, 0, 0]}
		position={[5, 0, 0]}
		castShadow
	/>
	
	<SC.Mesh
		geometry={new THREE.TorusGeometry(10, 5, 50, 40, 7)}
		material={new THREE.MeshStandardMaterial({ color: 0x00ff33 })}
		scale={[0.1, 0.1, 0.1]}
		rotation={[0, 0, 0]}
		position={[0, 0, 0]}
		castShadow
	/>

</SC.Group>
