<script>
	import top_black_background from '$lib/images/top_black_background.png';
	

</script>

<header>
	<img src={top_black_background} alt="" class="image_background" />
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div id="title_container" >
		<a class="title" href='/'> DZIO</a>
		<a class="subtitle" href='/'> Bank</a>
	</div>
</header>

<style lang="sass">
	@import '../styles/vars'
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
		.subtitle 
			font-size: 1.6rem
			color: $primary_color

		.title, .subtitle
			display: block
			cursor: pointer
			text-decoration: none
</style>
