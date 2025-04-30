<script>
	import '../app.css';

	let { children } = $props();
	
	
</script>
<!-- <nav class="z-100 absolute w-full">
	    <div class="m-auto mt-5 rounded-[93px] bg-[#760B02] p-5 w-[60%] flex justify-evenly text-white text-3xl font-bold backdrop-blur-sm text-shadow-lg/30">
	        <a class="underline underline-offset-8" href="/">Home</a>
	        <a class="underline underline-offset-8" href="/random">Random</a>
	        <a class="underline underline-offset-8" href="/result">Photobooth</a>
	    </div>
</nav> -->
{@render children()}
