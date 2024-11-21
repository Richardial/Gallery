<script>
	import { goto, pushState } from '$app/navigation';
	import { authenticated } from '$lib/stores/auth.js';
	import { BASE_URL } from '../../api/constants';

	let auth = false;
	let currentError = '';
	let correo = '';
	let contrasena = '';
	let correo2 = '';
	let contrasena2 = '';

	let nombre = '';
	let apellido = '';
	authenticated.subscribe((a) => (auth = a));

	const getCredentials = async () => {
		const params = { correo, contrasena };
		const url = `${BASE_URL}/credentials?${new URLSearchParams(params).toString()}`;
		goto(url);

		try {
			const response = await fetch(url, {
				method: 'GET',
				headers: {
					'Content-Type': 'application/json'
				},
				credentials: 'include'
			});

			const content = await response.json();
			console.log(content);

			if (response.status < 299) {
				nombre = content.correo;
				apellido = content.apellido;
				correo2 = content.correo;
				contrasena2 = content.contrasena;
			} else {
				currentError = 'Correo o contraseña incorrectos';
				console.log(currentError);
			}
		} catch (error) {
			currentError = 'Error xd';
			console.log(error);
		}
	};
</script>

{#if auth}
	<main>
		<section>
			<h2>Ver detalles de la cuenta</h2>
			<form on:submit|preventDefault={getCredentials}>
				<input
					type="text"
					autocomplete="email"
					required
					placeholder="Correo electrónico"
					bind:value={correo}
				/>
				<input
					type="password"
					autocomplete="current-password"
					required
					placeholder="Contraseña"
					bind:value={contrasena}
				/>
				<input class="boton" type="submit" value="Ver detalles" />
			</form>
			<p>Nombre: {nombre}</p>
			<p>Apellido: {apellido}</p>
			<p>Contraseña: {contrasena2}</p>
			<p>Correo: {correo2}</p>
		</section>
	</main>
{:else}
	<h1>No tienes acceso aca hijo de puta</h1>
{/if}

<style>
	main {
		width: 100%;
		height: 88vh;
		display: flex;
		justify-content: center;
	}

	section {
		width: 30%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	input {
		width: 100%;
		margin-top: 15px;
		margin-bottom: 15px;
		background-color: #332e2e;
		color: #ffffff;
		outline: none;
		border-top: none;
		border-left: none;
		border-right: none;
		border-color: #ffffff;
		font-size: 20px;
		font-weight: 400;
		font-family: inherit;
		padding: 5px;
	}

	.boton {
		width: 100%;
		border: solid;
		color: white;
		border-color: #ffffff;
		transition-duration: 0.5s;
		cursor: pointer;
	}

	.boton:hover {
		background-color: white;
		color: #332e2e;
		transition-duration: 0.5s;
	}
</style>
