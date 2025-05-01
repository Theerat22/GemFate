<script>
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

	onMount(() => {
		full_sentence_local = JSON.parse(localStorage.getItem('myLocal')) || "Your fortune awaits...";
		console.log(full_sentence_local);
	});
</script>

<section class="relative min-h-screen overflow-hidden">
	<div class="flex flex-col bg-cover bg-no-repeat min-h-screen justify-center items-center" 
		 style="background-image: url('/bg-result.png')">

		<div class="flex flex-col p-5 text-center">
			<div class="relative flex flex-col items-center">
				<!-- Photo frame -->
				<div class="relative w-full max-w-md mx-auto">
					<img src="/photoframe.png" class="w-full h-auto shadow-2xl" alt="photo frame">
					
					<!-- User uploaded image -->
					{#if avatar}
					<div class="absolute inset-0 flex items-center justify-center">
						<div class="relative w-[81%] h-[51%] top-[-11%]">
							<img 
								src={avatar} 
								class="w-full h-full object-cover" 
								alt="user photo"
							>
						</div>
					</div>
					{/if}
					
					<!-- Fortune text -->
					<div class="absolute bottom-[13%] left-0 right-0 mx-auto w-[80%] px-4">
						<p class="font-prompt text-base text-xl sm:text-4lg lg:text-xl text-black text-center">
							"{full_sentence_local}"
						</p>
					</div>
				</div>
				
				<!-- Upload button -->
				<button
					class="mt-4 duration-500 ease-in-out hover:scale-125"
					onclick={() => {
						fileinput.click();
					}}>
					<img src="/add.png" class="w-16 h-16 sm:w-20 sm:h-20" alt="add">
				</button>
				
				<input
					style="display:none"
					type="file"
					accept=".jpg, .jpeg, .png"
					onchange={(e) => onFileSelected(e)}
					bind:this={fileinput}
				/>
			</div>
		</div>
	</div>
</section>