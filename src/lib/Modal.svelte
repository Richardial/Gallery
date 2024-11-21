<script>
    // @ts-nocheck
	import { goto } from "$app/navigation";
	import { createEventDispatcher } from "svelte";
    import { BASE_URL } from "../api/constants";
	import { authenticated } from "./stores/auth";
    export let onClose;
    export let showModal;
    let correo = "";
    let contrasena = "";
    let currentError = "";


    const dispatch = createEventDispatcher();

    let auth = false;
    authenticated.subscribe((a) => (auth = a));

    function enableAlert(showAlert,success) {
		dispatch('showAlert', {
			showAlert,
            success
		});
	}

    const login = async() => {
        try {
            const response = await fetch(BASE_URL+'/login',{
                method: 'POST',
                headers:{
                    'Content-Type': 'application/json'
                },
                credentials: "include",
                body: JSON.stringify({correo,contrasena})
            })
        const content = await response.json();

        if(response.status<299){
            authenticated.set(true);
            goto("/Logged");
        }else{
            currentError = "Correo o contraseña incorrectos";
            console.log(currentError);
            enableAlert(true,false);   
        }

        }catch(error){
            currentError = "Error xd";
            console.log(currentError);
            enableAlert(true,false);   
        }
    }    

    $: {
		if (auth) {
			onClose();
		}
	}

</script>

{#if showModal}

<div class="modal">
    <div class="modal-content">
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <span class="close" on:click={onClose} on:keydown={onClose}>x</span>
        <h2>Iniciar Sesión</h2>
        <form on:submit|preventDefault={login}>
            <input type="text" autocomplete="email" required placeholder="Correo electrónico" bind:value={correo} />
            <input type="password" autocomplete="current-password" required placeholder="Contraseña" bind:value={contrasena} />
            <button class="button" type="submit">Ingresar</button>
        </form>
    </div>
</div>
{/if}

<style>
    .modal{
        position: fixed;
        z-index: 2;
        left: 0;
        top:0;
        width: 100%;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.514);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .modal-content{
        position: relative;
        background-color: #332e2e;
        color: white;
        padding-bottom: 80px;
        width: 25%;
        display: flex;
        flex-direction: column;
        align-items: center;
        -webkit-animation-name: modalAnimation;
		-webkit-animation-duration: 0.7s;
		animation-name: modalAnimation;
		animation-duration: 0.7s;
        overflow: hidden;
        
    }

    .close{
        position: absolute;
        top: 10px;
        right: 10px;
        font-size: 25px;
        cursor:pointer;
    }

    h2{
        margin-bottom: 50px;
    }

    form{
        width: 80%;
        max-width: 400px;
    }

    input{
        width: 100%;
        background-color: #332e2e;    
        font-size: 18px;
        color: white;
        margin-top: 30px;
        margin-top: 30px;
		border-top: none;
		border-left: none;
		border-right: none;
		border-color: white;
        font-family: inherit;
		outline: none;
    }

    .button{
        margin-top: 50px;
        width: 100%;
        background-color: #332e2e;
        padding: 10px;
        border-style: solid;
        border-color: white;
        color: white;
        font-family: inherit;
        font-size: 18px;
        cursor: pointer;
    }

    .button:hover{
        background-color: white;
        color: #332e2e;
    }

    @keyframes modalAnimation {
		from {
			top: -300px;
		}
		to {
			top: 0;
		}
	}

	@-webkit-keyframes modalAnimation {
		from {
			top: -300px;
		}
		to {
			top: 0;
		}
	}

</style>