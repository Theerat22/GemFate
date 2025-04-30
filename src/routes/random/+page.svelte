<script>
	import { once } from 'svelte/legacy';
	import Layout from '../+layout.svelte';
	import Modal from '$lib/Modal.svelte';

	/** @type {{ data: import('./$types').PageData }} */
	let { data } = $props();

	let full_sentence = 'ได้เพื่อนใหม่เป็น';
	let showModal = $state(false);
	let showModal2 = $state(false);
	let showModal3 = $state(false);
	let showModal4 = $state(false);
	let gender_rand = $state('');
	let acc_rand = $state('');
	let camp_rand = $state('');
	let house_rand = $state('');

	const gender_img = ['/male.png', '/female.png'];

	const gender = ['ผู้ชาย', 'ผู้หญิง'];
	const accesories = ['ใส่แว่นตา', 'ใส่นาฬิกา', 'ใส่เสื้อกันหนาว'];
	const houses = ['อยู่บ้าน Drop ', 'อยู่บ้าน Pro ', 'อยู่บ้าน Re ', 'อยู่บ้าน Tire '];
	const camp = [
		'และอยู่ค่าย Webgarnetic',
		'และอยู่ค่าย Infra',
		'และอยู่ค่าย Data',
		'และอยู่ค่าย Game'
	];

	// Random
	function getRandomInt(max) {
		return Math.floor(Math.random() * max);
	}

	const get_full_sentence = () => {
		alert(full_sentence);
	};
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center gap-3 bg-[url('/bg-random.png')] bg-cover bg-no-repeat"
>
	<div class="grid grid-cols-4 justify-center gap-16">
		<!-- Gender -->
		{#if !gender_rand}
			<button
				onclick={() => {
					gender_rand = gender[getRandomInt(2)];
					full_sentence += gender_rand;
					showModal = true;
					console.log(house_rand);
				}}
				class="mt-2 transition duration-300 hover:scale-110"
			>
				<img src="/rocks/rock1.png" alt="rock1" class="w-[400px]" />
			</button>
		{:else if gender_rand == 'ผู้ชาย'}
			<img src="/gems/male.png" alt="gem1" class="w-[400px]" />
		{:else if gender_rand == 'ผู้หญิง'}
			<img src="/gems/female.png" alt="gem1" class="w-[400px]" />
		{/if}

		<Modal bind:showModal>
			{#if gender_rand == 'ผู้ชาย'}
				<img src="/modals/male.png" alt="gem1" />
				
			{:else if gender_rand == 'ผู้หญิง'}
				<img src="/modals/female.png" alt="gem1" class="z-0"/>
				

			{/if}
		</Modal>

		<!-- Acc -->
		{#if !acc_rand}
			<button
				onclick={() => {
					if (gender_rand) {
						acc_rand = accesories[getRandomInt(3)];
						full_sentence += acc_rand;
						showModal2 = true;
					}
				}}
				class="mt-2 transition duration-300 hover:scale-110"
			>
				<img src="/rocks/rock2.png" alt="rock1" class="w-[400px]" />
			</button>
		{:else if acc_rand == 'ใส่แว่นตา'}
			<img src="/gems/glasses.png" alt="gem1" class="w-[400px]" />
		{:else if acc_rand == 'ใส่นาฬิกา'}
			<img src="/gems/watch.png" alt="gem1" class="w-[400px]" />
		{:else if acc_rand == 'ใส่เสื้อกันหนาว'}
			<img src="/gems/cloth.png" alt="gem1" class="w-[400px]" />
		{/if}

		<Modal bind:showModal2>
			{#if acc_rand == 'ใส่แว่นตา'}
				<img src="/modals/glasses.png" alt="gem1" />
			{:else if acc_rand == 'ใส่นาฬิกา'}
				<img src="/modals/watch.png" alt="gem1" />
			{:else if acc_rand == 'ใส่เสื้อกันหนาว'}
				<img src="/modals/cloth.png" alt="gem1" />
			{/if}
		</Modal>

		{#if !house_rand}
			<button
				onclick={() => {
					if (acc_rand) {
						house_rand = houses[getRandomInt(4)];
						full_sentence += house_rand;
						showModal3 = true;
						console.log(house_rand);
					}
				}}
				class="mt-2 transition duration-300 hover:scale-110"
			>
				<img src="/rocks/rock3.png" alt="rock1" class="w-[400px]" />
			</button>
		{:else if house_rand == 'อยู่บ้าน Drop '}
			<img src="/gems/drop.png" alt="gem1" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Pro '}
			<img src="/gems/pro.png" alt="gem1" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Re '}
			<img src="/gems/re.png" alt="gem1" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Tire '}
			<img src="/gems/tine.png" alt="gem1" class="w-[400px]" />
		{/if}

		<Modal bind:showModal3>
			{#if house_rand == 'อยู่บ้าน Drop '}
				<img src="/modals/drop.png" alt="gem1" />
			{:else if house_rand == 'อยู่บ้าน Pro '}
				<img src="/modals/pro.png" alt="gem1" />
			{:else if house_rand == 'อยู่บ้าน Re '}
				<img src="/modals/re.png" alt="gem1" />
			{:else if house_rand == 'อยู่บ้าน Tire '}
				<img src="/modals/tire.png" alt="gem1" />
			{/if}
		</Modal>

		{#if !camp_rand}
			<button
				onclick={() => {
					if (house_rand) {
						camp_rand = camp[getRandomInt(4)];
						full_sentence += camp_rand;
						showModal4 = true;
						console.log(house_rand);
						const result = localStorage.setItem('myLocal', JSON.stringify(full_sentence));
					}
				}}
				class="mt-2 transition duration-300 hover:scale-110"
			>
				<img src="/rocks/rock4.png" alt="rock1" class="w-[400px]" />
			</button>
		{:else if camp_rand == 'และอยู่ค่าย Webgarnetic'}
			<img src="/gems/web.png" alt="gem1" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Infra'}
			<img src="/gems/infra.png" alt="gem1" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Data'}
			<img src="/gems/data.png" alt="gem1" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Game'}
			<img src="/gems/game.png" alt="gem1" class="w-[400px]" />
		{/if}

		<Modal bind:showModal4>
			{#if camp_rand == 'และอยู่ค่าย Webgarnetic'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img src="/result_button.png" alt="gem1" />
				</a>
				<img src="/modals/web.png" alt="gem1" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Infra'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img src="/result_button.png" alt="gem1" />
				</a>
				<img src="/modals/infra.png" alt="gem1" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Data'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img src="/result_button.png" alt="gem1" />
				</a>
				<img src="/modals/data.png" alt="gem1" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Game'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img src="/result_button.png" alt="gem1" />
				</a>
				<img src="/modals/game.png" alt="gem1" />
				
			</div>
			{/if}
		</Modal>
	</div>

	<h1 class="font-prompt mt-20 text-7xl font-bold text-white">
		โปรดเลือกเพื่อดำเนินการจับคู่ของคุณ
	</h1>
	<!-- <button onclick={get_full_sentence}>full sentence</button> -->
</div>
