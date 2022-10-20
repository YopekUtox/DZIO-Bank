<script lang="ts">
	/* Import assets */
	import config from '$lib/images/config.png';
	import newCode from '$lib/images/new_code.png';
	import phone from '$lib/images/phone.png';
	import copy from '$lib/images/copy.png';
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';

	const fetchBLIK = () => {
		// currentBlik will be fetched from API
		return Math.floor(Math.random() * (99_99_99 - 10_00_00) + 10_00_00).toString();
	};
	let currentBlik = writable(' ');
	let blik = '';
	const maxSeconds = 120;
	let secondsRemaining: number = 5;
	let percentage: number = secondsRemaining / maxSeconds;
	let firstPart: string = '.   .   .';
	let secondPart: string = '.   .   .';
	let transitionDuration = 1;
	currentBlik.subscribe(
		(value) => {
			blik = value;
			firstPart = value.slice(0, 3);
			secondPart = value.slice(3, 6);
		},
		(val) => {
			firstPart = '.   .   .';
			secondPart = '.   .   .';
		}
	);
	onMount(() => {
		
		currentBlik.update(fetchBLIK);
		// secondsRemaining will be fetched from API

		percentage = secondsRemaining / maxSeconds;
		let expirationInterval = setInterval(() => {
			transitionDuration = 1;
			if (secondsRemaining === 0) {
				blikUpdate();
				return;
			}
			secondsRemaining -= 1;
			percentage = secondsRemaining / maxSeconds;
		}, 1000);
	});

	const onRefreshCodeClick = () => {
		blikUpdate();
	};

	interface ICopyMessages {
		default: string;
		success: string;
		error: string;
	}
	const copyMessages: ICopyMessages = {
		default: 'Kopiuj kod',
		success: 'Kod skopiowany',
		error: 'Błąd kopiowania'
	};
	let currentMessage: 'default' | 'success' | 'error' = 'default';
	const onCopyCodeClick = async () => {
		const message = await navigator.clipboard
			.writeText(blik)
			.then(() => 'success')
			.catch(() => 'error');
		currentMessage = message as 'success' | 'error';
		setTimeout(() => (currentMessage = 'default'), 3000);
	};

	function blikUpdate() {
		currentBlik.update(fetchBLIK);
		secondsRemaining = maxSeconds;
		percentage = secondsRemaining / maxSeconds;
		transitionDuration = 0.1;
	}
</script>

<section>
	<p class="title">Kod BLIK wygaśnie za</p>
	<div id="blik_expiration_container">
		<div class="meter" id="expire_bar">
			<span
				id="progress_bar"
				style="width: 100%; --scale_x_val: {percentage}; --transition_duration: {transitionDuration}s"
			/>
		</div>
		<span id="time_left"> {secondsRemaining.toString().padStart(3, '\u00A0')} s</span>
	</div>
	<div id="blik_number_container">
		<p class="title">Kod BLIK</p>
		<div id="numbers">
			<span class="number_part">
				{#if firstPart} {firstPart} {:else} . . . {/if}
			</span>
			<span class="number_part">
				{#if secondPart} {secondPart} {:else} . . . {/if}</span
			>
		</div>
	</div>

	<div id="blik_actions_container">
		<div class="blik_row">
			<button type="button" id="new_blik_code" class="blik_button" on:click={onRefreshCodeClick}>
				<img src={newCode} alt="Wygeneruj nowy kod" class="button_icon" />
				<span class="button_desc">Nowy kod</span>
			</button>
			<button type="button" id="copy_blik_code" class="blik_button" on:click={onCopyCodeClick}>
				<img src={copy} alt="Skopiuj kod" class="button_icon" />
				<span class="button_desc">{copyMessages[currentMessage]}</span>
			</button>
		</div>
		<!--
		<div class="blik_row">
			<button type="button" id="config_icon" class="blik_button">
				<img src={config} alt="Konfiguracja" class="button_icon" />
			</button>
			<button type="button" id="blik_for_phone" class="blik_button">
				<img src={phone} alt="Na telefon" class="button_icon" />
				<span class="button_desc">Blik na telefon</span>
			</button>
		</div>
        -->
	</div>
</section>
<footer>
	<a href="https://blik.com/pierwsze-kroki-z-blikiem" id="about_blik" class="title" target="_blank"
		>Jak działa BLIK?</a
	>
</footer>

<style lang="sass">

$font-size: 1.3rem
@import '../../styles/vars'
.title
    display: block
    font: 1.5rem $primary-font
    color: $primary-color
    margin: 0
    text-align: left
section 
    overflow: hidden
    position: relative
    display: grid
    grid-template-rows: repeat(auto-fit, minmax(100px,1fr))
    align-items: center
    grid-gap: 1rem
    padding: 1rem
    @media screen and (min-width: 768px) 
        justify-content: center
        grid-template-columns: repeat(1, minmax(500px, 700px))
    
.blik_button
    background: #3db8f519
    font: $font-size $primary-font
    color: $primary-color
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
    cursor: pointer
    

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
        

#blik_number_container
    display: flex
    flex-flow: column wrap
    align-items: center
    justify-content: center
    
    .title
        align-self: flex-start
    #numbers
        font: 4.5rem $primary-font
        color: $primary-color

#blik_expiration_container
    display: flex
    flex-flow: row nowrap
    justify-content: center
    align-items: center
    grid-gap: 1rem
    #expire_bar
        margin: 0
    #time_left
        font: 1.3rem $primary-font
        color: $primary-color
.meter
    flex: 10
    box-sizing: content-box
    height: 10px

    position: relative

    background-color:  $secondary-color
    border-radius: 25px
    padding: 5px

    & > span
        
        display: block
        height: 100%
        border-radius: 20px
        position: relative
        overflow: hidden

        &:after
            transition: transform var(--transition_duration) linear 
            content: ""
            position: absolute
            top: 0
            left: 0
            bottom: 0
            right: 0
            background: $primary-color
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
    color: $primary-color




</style>
