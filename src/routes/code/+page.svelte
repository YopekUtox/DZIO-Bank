<script lang="ts">
	import fingerPrintImage from '$lib/images/finger_print.png';
	const handlePasswordInput = (event: any) => {
		const entry = Number(event.currentTarget?.getAttribute('data-value'));
	};
	const spanList = [
		...Array(9)
			.fill(0)
			.map((_, index) => index + 1),
		'',
		0
	];
</script>

<p id="title">Wpisz kod kod dostępu</p>

<div class="password_entry_container">
	<span class="active password_entry">&#8729;</span>
	<span class="password_entry">&#8729;</span>
	<span class="password_entry">&#8729;</span>
	<span class="password_entry">&#8729;</span>
</div>

<div class="entries_container">
	{#each spanList as span}
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<span class="entry" on:click={handlePasswordInput} data-value={span === '' ? null : span}>
			<span class="entry_content">{span}</span>
		</span>
	{/each}
	<span class="entry">
		<a href="/fingerprint" class="entry_content">
			<img src={fingerPrintImage} alt="fngprint" class="entry_image" /></a
		>
	</span>
</div>
<footer>
    <p id="forgot_password">Nie pamiętasz kodu dostępu?</p>
</footer>
<style lang="sass">

#title, #forgot_password
    text-align: center
    font-size: 1.5rem
.password_entry_container
    overflow: hidden
    display: flex
    flex-flow: row nowrap
    grid-gap: 2rem
    font-size: 2rem
    align-items: center
    justify-content: center
    padding: 0
    user-select: none
    .password_entry
        font-size: 8rem
    .active
        transform: scale(2)
.entries_container
    display: grid
    grid-template-rows: repeat(4, 100px)
    grid-template-columns: repeat(3, 100px)
    align-items: center
    justify-items: center
    justify-content: center
    padding: 0
    margin: 0
    .entry
        font-size: 2rem
        cursor: pointer
        width: 100%
        height: 100%
        display: flex
        flex-flow: row nowrap
        align-items: center
        justify-content: center
        a
            padding: 1rem
        a:has(.entry_image)
            cursor: pointer
        .entry_image
            max-width: 100%
            max-height: 100%
            object-fit: contain
        &:not([data-value])
            cursor: context-menu            
        &[data-value]:hover
            background-color: yellow

</style>
