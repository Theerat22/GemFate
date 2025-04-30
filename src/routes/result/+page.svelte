<script>
	// If both `csr` and `ssr` are `false`, nothing will be rendered!
	import { onMount } from 'svelte';

	/** @type {{ data: import('./$types').PageData }} */

	let { data } = $props();
	let avatar = $state('');
	let fileinput = $state();
	let full_sentence_local = $state('');
	let image_width = $state(0);

	const onFileSelected = (e) => {
		let image = e.target.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (e) => {
			avatar = e.target.result;
		};
	};

	let x = $state("");

	onMount(() => {
		full_sentence_local = JSON.parse(localStorage.getItem('myLocal'));
		// alert(full_sentence_local)
		console.log(full_sentence_local);
		// let x = 

	});
</script>

<section class="relative min-h-screen overflow-hidden ">
	<div class="flex flex-col bg-cover bg-no-repeat min-h-screen justify-center items-center" 
		 style="background-image: url('/bg-result.png')">

		<div class="flex flex-col p-5 text-center">
			<!-- <h1 class="mb-10 font-bold text-3xl">Upload Image</h1> -->

			{#if avatar}
				<!-- <div class="m-auto mt-25 h-[700px] w-[500px] bg-[#FFD3D3]">
					<div class="flex justify-center">
						<img src="gemfatephoto.png" />
					</div>
					<img class="m-auto h-[386px] w-[404px] object-cover " src={avatar} alt="name">
					<div class="m-auto flex justify-center">
						<img src="icon.png" class="m-5" />
					</div><img src="photogem1.png" class="translate-x-[400px] -translate-y-[500px]" />
					<img src="photogem2.png" class="-translate-x-[50px] -translate-y-[450px]" />
					<img src="photogem3.png" class="translate-x-[470px] -translate-y-[325px]" />
					<img src="photogem4.png" class="-translate-x-[50px] -translate-y-[200px]" />

					<p class="-translate-y-[300px]  text-xl font-prompt">{full_sentence_local}</p>
				</div> -->

				<div class="flex flex-col items-center text-center">
					<img src="/photoframe.png" class="scale-80 z-0 shadow-2xl" alt="frmae">
					<img src={avatar} class="absolute scale-80 z-30 w-[323px] h-[308px] translate-y-[99px] sm:translate-y-[99px] lg:translate-y-[570px] object-cover" alt="frmae">
	
					<div 
					class="absolute transform z-20 w-[330px] translate-y-[430px] sm:translate-y-[570px] lg:translate-y-[570px] "
					>
					<p class="absolute font-prompt text-lg text-black p-2 rounded text-center">
						"{full_sentence_local}"
					</p>
					</div>
				</div>
			{:else}
			<!-- <div class="m-auto mt-25 h-[700px] w-[500px] bg-[#FFD3D3]">
				<div class="flex justify-center">
					<img alt="" src="gemfatephoto.png" class="scale-70 sm:scale-30 lg:scale-69"/>
				</div>
				<div class="m-auto h-[386px] w-[404px] bg-white"></div>
				<div class="m-auto flex justify-center">
					<img alt="" src="icon.png" class="m-5" />
				</div>
				<img alt="" src="photogem1.png" class="translate-x-[400px] -translate-y-[500px]" />
				<img alt="" src="photogem2.png" class="-translate-x-[50px] -translate-y-[450px]" />
				<img alt="" src="photogem3.png" class="translate-x-[470px] -translate-y-[325px]" />
				<img alt="" src="photogem4.png" class="-translate-x-[50px] -translate-y-[200px]" />

				<p class="-translate-y-[300px]  text-xl font-prompt">{full_sentence_local}</p>
			</div> -->
			<div class="flex flex-col items-center text-center">
				<img src="/photoframe.png" class="scale-80 z-0 shadow-2xl" alt="frmae">

				<!-- <div class="absolute z-50">
					<img alt="" src="photogem1.png" class="translate-x-[400px] -translate-y-[500px]" />
					<img alt="" src="photogem2.png" class="-translate-x-[50px] -translate-y-[450px]" />
					<img alt="" src="photogem3.png" class="translate-x-[470px] -translate-y-[325px]" />
					<img alt="" src="photogem4.png" class="-translate-x-[50px] -translate-y-[200px]" />
				</div> -->

				<div 
				class="absolute transform z-20 w-[330px] translate-y-[430px] sm:translate-y-[570px] lg:translate-y-[570px] "
				>
				<p class="absolute font-prompt text-lg text-black p-2 rounded text-center">
					"{full_sentence_local}"
				</p>
				</div>
			</div>
			


			<button
			class="mx-auto duration-500 ease-in-out hover:scale-125"
			onclick={() => {
				fileinput.click();
			}}>
			<img src="/add.png" class="scale-70 pb-10" alt="add">
			</button
	>
	<input
		style="display:none"
		type="file"
		accept=".jpg, .jpeg, .png"
		onchange={(e) => onFileSelected(e)}
		bind:this={fileinput}
	/>
			{/if}
		</div>
	</div>
</section>


<!-- <button
	class="mt-4 bg-green-400 p-2 font-bold"
	onclick={() => {
		fileinput.click();
	}}>อัปโหลดรูป</button
>
<input
	style="display:none"
	type="file"
	accept=".jpg, .jpeg, .png"
	onchange={(e) => onFileSelected(e)}
	bind:this={fileinput}
/> -->