<script>
	import config from '$lib/images/config.png';
	import newCode from '$lib/images/new_code.png';
	import phone from '$lib/images/phone.png';
	import copy from '$lib/images/copy.png';
</script>

<section>
	<p class='title'>Kod BLIK wygaśnie za</p>
    <div id='blik_expiration_container'> 
        
        <div class="meter" id='expire_bar'>
            <span style="width: 100%; --scale_x_val: {90}%"></span>
        </div>
        <span id='time_left'> 90 s</span>
    </div>
	<div id="blik_number_container">
        <p class='title'>Kod BLIK</p>
        <div id='numbers'>
            <span class='number_part'> 213 </span>
            <span class='number_part'> 769 </span>
        </div>
	</div>

	<div id="blik_actions_container">
		<div class="blik_row">
			<button type='button' id="new_blik_code" class="blik_button">
				<img src={newCode} alt="Wygeneruj nowy kod" class="button_icon" />
				<span class='button_desc'>Nowy kod</span>
			</button>
			<button type='button' id="copy_blik_code" class="blik_button">
				<img src={copy} alt="Skopiuj kod" class="button_icon" />
				<span class='button_desc'>Kopiuj kod</span>
			</button>
		</div>
		<div class="blik_row">
			<button type='button' id="config_icon" class="blik_button">
				<img src={config} alt="Konfiguracja" class="button_icon" />
			</button>
			<button type='button' id="blik_for_phone" class="blik_button">
				<img src={phone} alt="Na telefon" class="button_icon" />
				<span class='button_desc'>Blik na telefon</span>
			</button>
		</div>
	</div>

</section>
<footer>
    <a href='https://blik.com/pierwsze-kroki-z-blikiem' id='about_blik' class='title'>Jak działa BLIK?</a>
</footer>
<style lang="sass">

$font-size: 1.3rem

.title
    display: block
    font: 1.5rem sans-serif
    color: #3fbdf1ff
    margin: 0
    text-align: left
section 
    overflow: hidden
    position: relative
    display: grid
    grid-template-rows: repeat(auto-fit, minmax(100px,1fr))
    align-items: center
    padding: 1rem
.blik_button
    background: #3db8f519
    font: $font-size sans-serif
    color: #3fbdf1ff
    border: none
    outline: none
    min-height: 80px
    min-width: 80px
    border-radius: 1rem
    display: flex
    flex-flow: row nowrap
    justify-content: center
    align-items: center
    padding: 0.8rem
    grid-gap: 0.5rem
    

#blik_actions_container
    display: grid
    grid-template-rows: repeat(2, 50%)
    text-align: center
    grid-gap: 1rem
    .blik_row
        display: flex
        flex-flow: row nowrap
        align-items: center
        grid-gap: 1rem
        &:not(#config_icon) img
            height: $font-size
        #new_blik_code
            flex: 2
        #copy_blik_code
            flex: 2
        #config_icon
            flex: 1
            img
                height: auto
        #blik_for_phone
            flex: 4
        

#blik_number_container
    display: flex
    flex-flow: column wrap
    align-items: center
    justify-content: center
    
    .title
        align-self: flex-start
    #numbers
        font: 4.5rem sans-serif
        color: #3fbdf1ff

#blik_expiration_container
    display: flex
    flex-flow: row nowrap
    justify-content: center
    align-items: center
    grid-gap: 1rem
    #expire_bar
        margin: 0
    #time_left
        font-size: 1.3rem
        color: #3fbdf1ff
.meter
    flex: 10
    box-sizing: content-box
    height: 10px

    position: relative

    background-color:  #9bdcf8
    border-radius: 25px
    padding: 5px

    & > span
        display: block
        height: 100%
        border-radius: 20px
        position: relative
        overflow: hidden

        &:after
            content: ""
            position: absolute
            top: 0
            left: 0
            bottom: 0
            right: 0
            background: #3fbdf1ff
            z-index: 1
            animation: move 2s linear infinite
            transform-origin: left
            transform: scaleX(var(--scale_x_val))
            border-radius: 20px
            overflow: hidden
#about_blik
    display: block
    text-align: center
    margin: 2rem
    font-weight: bold
    text-decoration: none
    color: #3fbdf1ff




</style>
