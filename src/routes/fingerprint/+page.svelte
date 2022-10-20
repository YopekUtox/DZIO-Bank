<script>
	import fingerPrintImage from '$lib/images/finger_print.png';
</script>

<section id="finger_print_unlock">
	<p id="title">Odblokuj odciskiem palca</p>

	<img src={fingerPrintImage} alt="Zaloguj się odciskiem palca" />

</section>
<footer>
    <a href="/code"> Tym razem użyj kodu dostępu</a>
</footer>
<style lang="sass">
@import '../../styles/vars'
#finger_print_unlock
    display: flex
    flex-flow: column nowrap
    justify-content: center
    align-items: center
    grid-gap: 2rem
#title, a
    text-align: center
    font: 1.5rem $primary-font
img
    padding: 5rem
footer
    text-align: center
    a
        display: block
        text-align: center
        margin: 2rem
        font-weight: bold
        text-decoration: none
        color: $primary-color
</style>
