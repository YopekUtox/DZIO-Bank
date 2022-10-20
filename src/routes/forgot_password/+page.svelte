<script lang='ts'>
    const handleSubmit = (ev: SubmitEvent) => {
        ev.preventDefault();
        const forgotPasswordData = new FormData(ev.target as HTMLFormElement);
        // There will be fetch to post 
    }
</script>

<section>
    <form method="post" id='reset_password_form' on:submit={handleSubmit}>
        <label for='user_email' class='label'> Podaj swój e-mail </label>
        <input type='email' name='user_email' id='user_email_input' />
        <input type='submit' id='reset_password_submit' value='Wyślij nowy kod'> 
        <p class='error_message'> </p>
    </form>
</section>

<style lang='sass'>
section , #reset_password_form
    overflow: hidden
    position: relative
    display: flex
    flex-flow: column nowrap
    justify-content: center
    align-items: center
    grid-gap: 1rem
.label
    display: block
    font: 1.5rem sans-serif
    color: #3fbdf1
    margin: 0
    text-align: left
#user_email_input
    font: 1.5rem sans-serif
    padding: 0.4rem
    border-radius: 0.4rem
    border-style: solid
    border-color: #3fbdf1
    &:focus, &:active
        outline: none
#reset_password_submit
    background: #3db8f519
    font: 1.2rem sans-serif
    color: #3fbdf1
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
</style>