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
				<img alt="" src="/rocks/rock1.png" class="w-[400px]" />
			</button>
		{:else if gender_rand == 'ผู้ชาย'}
			<img alt="" src="/gems/male.png" class="w-[400px]" />
		{:else if gender_rand == 'ผู้หญิง'}
			<img alt="" src="/gems/female.png" class="w-[400px]" />
		{/if}

		<Modal bind:showModal>
			{#if gender_rand == 'ผู้ชาย'}
				<img alt="" src="/modals/male.png" />
				
			{:else if gender_rand == 'ผู้หญิง'}
				<img alt="" src="/modals/female.png" class="z-0"/>
				

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
				<img alt="" src="/rocks/rock2.png" class="w-[400px]" />
			</button>
		{:else if acc_rand == 'ใส่แว่นตา'}
			<img alt="" src="/gems/glasses.png" class="w-[400px]" />
		{:else if acc_rand == 'ใส่นาฬิกา'}
			<img alt="" src="/gems/watch.png" class="w-[400px]" />
		{:else if acc_rand == 'ใส่เสื้อกันหนาว'}
			<img alt="" src="/gems/cloth.png" class="w-[400px]" />
		{/if}

		<Modal bind:showModal2>
			{#if acc_rand == 'ใส่แว่นตา'}
				<img alt="" src="/modals/glasses.png" />
			{:else if acc_rand == 'ใส่นาฬิกา'}
				<img alt="" src="/modals/watch.png" />
			{:else if acc_rand == 'ใส่เสื้อกันหนาว'}
				<img alt="" src="/modals/cloth.png" />
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
				<img alt="" src="/rocks/rock3.png" class="w-[400px]" />
			</button>
		{:else if house_rand == 'อยู่บ้าน Drop '}
			<img alt="" src="/gems/drop.png" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Pro '}
			<img alt="" src="/gems/pro.png" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Re '}
			<img alt="" src="/gems/re.png" class="w-[400px]" />
		{:else if house_rand == 'อยู่บ้าน Tire '}
			<img alt="" src="/gems/tine.png" class="w-[400px]" />
		{/if}

		<Modal bind:showModal3>
			{#if house_rand == 'อยู่บ้าน Drop '}
				<img alt="" src="/modals/drop.png" />
			{:else if house_rand == 'อยู่บ้าน Pro '}
				<img alt="" src="/modals/pro.png" />
			{:else if house_rand == 'อยู่บ้าน Re '}
				<img alt="" src="/modals/re.png" />
			{:else if house_rand == 'อยู่บ้าน Tire '}
				<img alt="" src="/modals/tire.png" />
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
				<img alt="" src="/rocks/rock4.png" class="w-[400px]" />
			</button>
		{:else if camp_rand == 'และอยู่ค่าย Webgarnetic'}
			<img alt="" src="/gems/web.png" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Infra'}
			<img alt="" src="/gems/infra.png" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Data'}
			<img alt="" src="/gems/data.png" class="w-[400px]" />
		{:else if camp_rand == 'และอยู่ค่าย Game'}
			<img alt="" src="/gems/game.png" class="w-[400px]" />
		{/if}

		<Modal bind:showModal4>
			{#if camp_rand == 'และอยู่ค่าย Webgarnetic'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img alt="" src="/result_button.png" />
				</a>
				<img alt="" src="/modals/web.png" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Infra'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img alt="" src="/result_button.png" />
				</a>
				<img alt="" src="/modals/infra.png" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Data'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img alt="" src="/result_button.png" />
				</a>
				<img alt="" src="/modals/data.png" />
				
			</div>
			{:else if camp_rand == 'และอยู่ค่าย Game'}
			<div class="flex flex-col justify-center items-center">
				<a href="/result" class="mt-1">
					<img alt="" src="/result_button.png" />
				</a>
				<img alt="" src="/modals/game.png" />
				
			</div>
			{/if}
		</Modal>
	</div>

	<h1 class="font-prompt mt-20 text-7xl font-bold text-white">
		โปรดเลือกเพื่อดำเนินการจับคู่ของคุณ
	</h1>
	<!-- <button onclick={get_full_sentence}>full sentence</button> -->
</div>
