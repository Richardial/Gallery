<script>
	// @ts-nocheck
	import { goto } from '$app/navigation';

	import { authenticated } from '$lib/stores/auth';
	import { BASE_URL } from '../../api/constants';

	let correo;
	let contrasena;

	let auth = false;
	authenticated.subscribe((a) => (auth = a));

	const login = async () => {
		try {
			const response = await fetch(BASE_URL + '/login', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				credentials: 'include',
				body: JSON.stringify({ correo, contrasena })
			});
			const content = await response.json();

			if (response.status < 299) {
				authenticated.set(true);
				setTimeout(() => {
					goto('/Logged');
				}, 0);
			} else {
				currentError = 'Correo o contraseña incorrectos';
				console.log(currentError);
				enableAlert(true, false);
			}
		} catch (error) {
			currentError = 'Error xd';
			console.log(currentError);
			enableAlert(true, false);
		}
	};

	
</script>

<main>
	<header class="centrar">
		<h2>Iniciar Sesión</h2>
	</header>
	<section class="formulario">
		<article class="centrar temporal">
			<div class="contenedor">
				<form on:submit|preventDefault={login}>
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
					<input class="boton" type="submit" value="Ingresar" />
				</form>
			</div>
		</article>
		<div class="linea"></div>
		<article class="temporal">
			<p class="center-text">
				"Cada imagen es un susurro del bosque, un recordatorio de que en la naturaleza encontramos
				la paz que el alma busca y la belleza que los ojos anhelan."
			</p>
		</article>
	</section>
</main>

<style>
	main {
		width: 100%;
		height: 90vh;
	}

	.centrar {
		display: flex;
		justify-content: center;
	}

	.formulario {
		display: flex;
		width: 100%;
	}

	.temporal {
		width: 50%;
	}

	.center-text {
		text-align: center;
	}

	article {
		display: flex;
		align-items: center;
	}

	article .center-text {
		margin-left: 30%;
		margin-right: 30%;
	}

	h2 {
		margin: 0;
	}

	header h2 {
		font-size: 30px;
		padding: 40px 0px;
	}

	.contenedor {
		width: 60%;
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

	.linea {
		border-style: solid;
		border-top: none;
		border-bottom: none;
		border-width: 2px;
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
