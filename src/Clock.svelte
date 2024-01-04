<script>
	import { onMount } from 'svelte';
	let date = new Date();
	$: hour = date.getHours();
	$: min = date.getMinutes();
	$: sec = date.getSeconds();
	let dayOrNight = 'AM';
	
	onMount( () => {
		const interval = setInterval(() => {
			date = new Date();
			dayOrNight = (hour >= 12) ? "PM" : "AM";
		}, 1000);
	});
</script>

<style>
	section, .clockWrapper, .clockDisplay {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	section{
		height: 100vh;
		width: 100vw;
		overflow: hidden;
		background: black;
	}
	.clockWrapper {
		width: 75%;
		height: 50%;
		border-radius: 15px;
		background: #ffffff;
	}
	.clockDisplay {
		width: 99%;
		height: 99%;
		font-size: 5em;
		background: #059506;
		border-radius: 15px;
		color: #ffffff;
	}
</style>

<section>
	<div id='' class='clockWrapper'>
		<p class='clockDisplay'> 
			{hour - 12} : {min} : {sec} {dayOrNight}
		</p>
	</div>
</section>







