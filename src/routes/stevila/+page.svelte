<script lang="ts">
	let stevilo = 0;
	let sodo = true;
	let sezD: number[] = [];
	let vsD = 0;

	function jeSodo(num: number) {
		return num % 2 == 0;
	}
	function vsiDelitelji(num: number) {
		let del: number[] = [];
		for (let i = 0; i < num; i++) {
			if (num % i == 0) del.push(i);
		}
		return del;
	}
	function vsotaDeliteljev(num: number[]) {
		let vs = 0;
		for (const i of num) {
			vs += i;
		}
		return vs;
	}

	$: {
		sodo = jeSodo(stevilo);
		sezD = vsiDelitelji(stevilo);
		vsD = vsotaDeliteljev(sezD);
	}
</script>

<div class="flex flex-col gap-10 items-center justify-center pt-20">
	<div class="flex">
		<input
			bind:value={stevilo}
			class="border-2 border-blue-500 m-3 p-2 rounded-3xl text-4xl text-center"
			type="number"
		/>
	</div>
	<div class="grid grid-cols-4 text-3xl text-blue-100">
		<div>
			<p class="bg-blue-500 rounded-xl m-3 p-2">{sodo ? 'SODO' : 'LIHO'}</p>
		</div>

		<div class="bg-blue-500 rounded-xl m-3 p-2">
			<p>Delitelji:</p>
			<ul class="flex flex-wrap">
				{#each sezD as st}
					<li class="m-0.5 rounded-md p-0.5 bg-blue-100 text-blue-500">{st}</li>
				{/each}
				<li class="m-0.5 rounded-md p-0.5 bg-blue-100 text-blue-500">{stevilo}</li>
			</ul>
		</div>
		<div class="bg-blue-500 rounded-xl m-3 p-2">
			<p>Vsota del.</p>
			<p>{vsD + stevilo}</p>
		</div>
	</div>
</div>
