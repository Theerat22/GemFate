<<<<<<< HEAD
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
		<img src="logo.png" alt="Logo" class="h-20 sm:h-20" />
		<img src="itCamp.png" alt="IT Camp" class="h-12 sm:h-16" />
	  </div>
	  
	  <!-- Center Content -->
	  <div class="flex flex-col items-center justify-center flex-grow px-1 7">
		<img src="gemfatetitle.png" alt="Gem Fate Title" class="w-3/4 sm:w-2/4 lg:w-1/3 mb-10" />
		<button 
		  on:click={handleRandomClick} 
		  class="transition-transform duration-500 ease-in-out hover:scale-125 bg-transparent border-none p-0 cursor-pointer"
		>
		  <img src="button.png" alt="Start Button" class="w-40 sm:w-48 lg:w-56" />
		</button>
	  </div>
  
	</div>
  </section>
  
  <!-- 
	Optional: Add global styles
	In Svelte you can add styles here that will be scoped to this component
  -->
  <style>
	/* Add any additional component-specific styles here */
	/* These styles will be processed by Svelte and scoped to this component */
  </style>
=======



<div class="flex min-h-screen max-w-screen flex-col bg-[url(/bg-result.png)] bg-cover bg-no-repeat">
	<div class="flex justify-between overflow-hidden">
		<img alt="" src="logo.png" class="sm:scale-10 lg:scale-120"/> <img alt="" src="itCamp.png" class="m-10" />
	</div>
	<div class="flex flex-col items-center justify-center mt-20">
		<img alt="" src="gemfatetitle.png" class="sm:scale-40 lg:scale-150 "/>
		<a href="random" class="m-auto mt-50"
			><img alt="" src="button.png" class="sm:scale-10 lg:scale-100 duration-500 ease-in-out hover:scale-125" /></a
		>
	</div>       
</div>
>>>>>>> 2c28850f1ad2254de85a147845994a89b49d5e90
