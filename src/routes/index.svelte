<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	let spin = 0;
	SC.onFrame(() => {
		spin += 0.01;
	});
</script>

<SC.Canvas antialias background={new THREE.Color('gray')} fog={new THREE.FogExp2('white', 0.1)}>
	<SC.Mesh
		geometry={new THREE.BoxGeometry()}
		material={new THREE.MeshStandardMaterial({ color: 0x000000 })}
		scale={[2.5, 1.5, 0.02]}
		rotation={[0, spin, 0]}
		castShadow
	/>
	<SC.PerspectiveCamera position={[1, 1, 3]} />
	<SC.OrbitControls enableZoom={false} />
	<SC.AmbientLight intensity={0.6} />
	<SC.DirectionalLight intensity={0.8} position={[-2, 3, 2]} shadow={{ mapSize: [2048, 2048] }} />
</SC.Canvas>
