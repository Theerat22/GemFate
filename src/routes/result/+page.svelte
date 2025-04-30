<script>
	// If both `csr` and `ssr` are `false`, nothing will be rendered!
	import { onMount } from 'svelte';

	/** @type {{ data: import('./$types').PageData }} */

	let { data } = $props();
	let avatar = $state('');
	let fileinput = $state();
	let full_sentence_local = $state('');

	const onFileSelected = (e) => {
		let image = e.target.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (e) => {
			avatar = e.target.result;
		};
	};

	let x = $state("");

	// const putImage = () => {
	// 	let canvas = document.getElementById('canvas');
	// 	// let ctx = canvas.ge
	// 	let ctx = canvas.getContext('2d');
	// 	let img alt="" = document.getElementById('img alt=""');
	// 	ctx.drawImage(img alt="", 10, 10);

	// 	const dataURL = canvas.toDataURL();
	// 	console.log(dataURL);
	// 	const fullQuality = canvas.toDataURL('image/jpeg', 1.0);
	// };



	onMount(() => {
		full_sentence_local = JSON.parse(localStorage.getItem('myLocal'));
		// alert(full_sentence_local)
		console.log(full_sentence_local);
		// let x = 

	});
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center bg-[url('/bg-result.png')] bg-cover bg-no-repeat"
>
	<div class="flex flex-col p-5 text-center">
		<!-- <h1 class="mb-10 font-bold text-3xl">Upload Image</h1> -->

		{#if avatar}
			<!-- <canvas
				id="canvas"
				width="1000px"
				height="500px"
				class="z-0 h-[500px] w-[300px] items-center rounded-2xl bg-white px-8 pt-9"
			></canvas> -->
			<div class="m-auto mt-25 h-[700px] w-[500px] bg-[#FFD3D3]">
				<div class="flex justify-center">
					<img alt="" src="gemfatephoto.png" />
				</div>
				<img alt="" class="m-auto h-[386px] w-[404px] object-cover " src={avatar}>
				<div class="m-auto flex justify-center">
					<img alt="" src="icon.png" class="m-5" />
				</div><img alt="" src="photogem1.png" class="translate-x-[400px] -translate-y-[500px]" />
				<img alt="" src="photogem2.png" class="-translate-x-[50px] -translate-y-[450px]" />
				<img alt="" src="photogem3.png" class="translate-x-[470px] -translate-y-[325px]" />
				<img alt="" src="photogem4.png" class="-translate-x-[50px] -translate-y-[200px]" />

				<p class="-translate-y-[300px]  text-xl font-prompt">{full_sentence_local}</p>
			</div>

			<!-- Download Complete -->
			<!-- <button onclick={putImage} class="bg-pink-300 p-3">Click to console</button> -->
		{:else}
		<div class="m-auto mt-25 h-[700px] w-[500px] bg-[#FFD3D3]">
			<div class="flex justify-center">
				<img alt="" src="gemfatephoto.png" />
			</div>
			<div class="m-auto h-[386px] w-[404px] bg-white"></div>
			<div class="m-auto flex justify-center">
				<img alt="" src="icon.png" class="m-5" />
			</div><img alt="" src="photogem1.png" class="translate-x-[400px] -translate-y-[500px]" />
			<img alt="" src="photogem2.png" class="-translate-x-[50px] -translate-y-[450px]" />
			<img alt="" src="photogem3.png" class="translate-x-[470px] -translate-y-[325px]" />
			<img alt="" src="photogem4.png" class="-translate-x-[50px] -translate-y-[200px]" />

			<p class="-translate-y-[300px]  text-xl font-prompt">{full_sentence_local}</p>
		</div>

		<button
		class="mt-10 m-auto duration-500 ease-in-out hover:scale-125"
		onclick={() => {
			fileinput.click();
		}}>
		<img alt="" src="/add.png">
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