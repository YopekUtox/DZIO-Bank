<script>
	import banking_guy from '$lib/images/banking_guy.png';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<img src={banking_guy} alt="Bankuj" id="banking_guy_img" />
	<p>Bankuj po swojemu</p>
	<div class="buttons_container">
		<a href="/code" id="login_button" class="buttons__anchor"> Zaloguj </a>

		<a href="/blik" id="blik_button" class="buttons__anchor"> Kod BLIK </a>
	</div>
</section>

<style lang="sass">
	section 
		overflow: hidden
		position: relative
		display: flex
		flex-flow: column nowrap
		justify-content: center
		align-items: center
	
	.buttons_container 
		display: flex
		flex-flow: column nowrap
		color: white
		grid-gap: 1.2rem
		align-items: center
		margin-top: 3rem
	
	.buttons__anchor 
		padding: 1.2rem
		border-radius: 0.8rem
		font-size: 1.7rem
		color: white
		border: none
		width: 120%
		max-width: 90vw
		transform-origin: 50% 50%
		text-align: center
		text-decoration: none
	
	#login_button 
		width: 150%
		font-size: 2rem
		background-color: #3fbdf1
	
	#blik_button 
		background-color: #9bdcf8
	
	p 
		font: 1.5rem sans-serif
	
	#banking_guy_img 
		max-width: 90vw

</style>
