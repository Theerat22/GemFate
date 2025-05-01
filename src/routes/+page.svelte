<script>
	// You can add any necessary Svelte logic here
	import { onMount } from 'svelte';
	
	function handleRandomClick() {
	  window.location.href = '/random';
	}
  </script>
  
  <svelte:head>
	<title>Responsive Page</title>
  </svelte:head>
  
  <section class="relative min-h-screen overflow-hidden">
	<div class="flex flex-col bg-cover bg-no-repeat min-h-screen" 
		 style="background-image: url('/bg-result.png')">
	  
	  <!-- Header with logos -->
	  <div class="flex justify-between items-center px-4 py-4 sm:px-10">
		<img src="logo.png" alt="Logo" class="h-20 scale-100 sm:h-20 scale-125" />
		<img src="itCamp.png" alt="IT Camp" class="h-12 sm:h-16" />
	  </div>
	  
	  <!-- Center Content -->
	  <div class="flex flex-col items-center justify-center flex-grow px-1 7">
		<img src="gemfatetitle.png" alt="Gem Fate Title" class="w-3/4 scale-100 sm:w-2/4 scale-125 pb-10 lg:w-1/3 mb-10 "loading="lazy" />
		<button 
		  onclick={handleRandomClick} 
		  class="transition-transform duration-500 ease-in-out hover:scale-125 bg-transparent border-none p-0 cursor-pointer"
		>
		  <img src="button.png" alt="Start Button" class="w-40 sm:w-48 lg:w-56" />
		</button>
	  </div>
  
	</div>
  </section>