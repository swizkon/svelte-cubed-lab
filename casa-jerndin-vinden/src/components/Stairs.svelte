<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	export let position = [0, 0, 0];
	
	let steps = [ ];
	
	onMount(async () => {
		for(var i = 0 ; i < 10 ; i++){
			steps[i] = [0 - i * 40, 0 - i * 30, 320];
		}
	});

</script>

<SC.Group position={position}>

	{#each steps as step}
		<SC.Mesh
		geometry={new THREE.BoxGeometry(40, 30, 140)}
		material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
		scale={[1,1,1]}
		position={step}
		castShadow
	/>
	{/each}
	
</SC.Group>
