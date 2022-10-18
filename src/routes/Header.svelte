<script>
	import top_black_background from '$lib/images/top_black_background.png';
	

</script>

<header>
	<img src={top_black_background} alt="" class="image_background" />
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div id="title_container" >
		<span class="title" on:click={() => location.href = '/'}> DZIO</span>
		<span class="subtitle" on:click={() => location.href = '/'}> Bank</span>
	</div>
</header>

<style lang="sass">
	header 
		overflow: hidden
		position: relative
		display: flex
		flex-flow: column nowrap
		justify-content: center
		align-items: center
	
	.image_background 
		width: 120%
		max-height: 200px
	
	#title_container 
		position: absolute
		height: 200px
		width: 100%
		top: 20%
		text-align: center
	
	#title_container 
		.title 
			color: white
			font-size: 2rem
			display: block
			cursor: pointer
		.subtitle 
			font-size: 1.6rem
			color: #3fbdf1
			display: block
			cursor: pointer

</style>
