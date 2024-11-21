<script>
	import { goto } from '$app/navigation';

	// @ts-nocheck
	import Alert from './Alert.svelte';
	import Modal from './Modal.svelte';
	import { authenticated } from './stores/auth';

	let showModal = false;
	let showAlert = false;
	let success = false;

	let auth = false;

	authenticated.subscribe((a) => (auth = a));

	function toggleModal() {
		showModal = !showModal;
	}

	function closeAlert(){
		showAlert = false;
	}
	
	const logout = () => {
		authenticated.set(false);
		// goto("/");
	};

	function handleShowAlert(event){
		showAlert = event.detail.showAlert;
		success = event.detail.success;
		setTimeout(closeAlert,5000);
	}

</script>

<header class="navbar">
	<a href="/">
		<h1>Foto UdeC</h1>
	</a>
	<nav>
		<ul>
			<li><a href="Registro">Registrarse</a></li>
			{#if auth}
				<li><a href="/" on:click={logout}>Logeado</a></li>
			{:else}
				<!-- <li><a href="/Login" >Login</a></li> -->
				<li><a href="#Login" on:click={toggleModal}>Login</a></li>
			{/if}
		</ul>
	</nav>
</header>

<main>
	{#if showAlert}
		<Alert {success}/>
	{/if}
	<Modal {showModal} onClose={toggleModal} on:showAlert={handleShowAlert}/>
</main>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 12vh;
		/* padding-top: 20px;
		padding-bottom: 0px; */
	}

	nav {
		position: relative;
		margin: 0;
	}

	ul {
		margin: 0;
		margin-right: 50px;
		display: flex;
		list-style: none;
	}

	li {
		position: relative;
		margin: 0px;
		margin-left: 40px;
	}

	.navbar {
		background-color: #312e2c;
	}

	a {
		color: white;
		text-decoration: none;
		margin-left: 0px;
		font-size: 18px;
	}

	li a::before {
		position: absolute;
		content: ' ';
		left: 0;
		bottom: 0;
		width: 0px;
		height: 2px;
		background-color: white;
		transition-duration: 0.5s;
	}

	a:hover::before {
		width: 100%;
		transition-duration: 0.5s;
	}

	h1 {
		margin: 0;
		font-size: 30px;
		margin-left: 20px;
	}
</style>
