<script>
	
	// @ts-nocheck
	import { goto } from "$app/navigation";

	import { BASE_URL } from "../../api/constants";

	let nombre;
	let apellido;
	let correo;
	let contrasena;

	const registro = async() => {
        try {
            const response = await fetch(BASE_URL+'/register',{
                method: 'POST',
                headers:{
                    'Content-Type': 'application/json'
                },
                credentials: "include",
                body: JSON.stringify({nombre,apellido,contrasena,correo})
            })
        const content = await response.json();

        if(response.status<299){
			goto("/Logged");
        }else{
            currentError = "Error Interno";
        }

        }catch(error){
            // @ts-ignore
            currentError = "Error xd";
        }
    }
</script>

<main>
	<header class="centrar">
		<h2>Registrate para mas contenido</h2>
	</header>
	<section class="formulario">
		<article class="centrar temporal">
			<div class="contenedor">
				<form on:submit|preventDefault={registro}>
					<input type="text" name="Nombre" required placeholder="Nombre" bind:value={nombre}/>
					<input type="text" name="Apellido" required placeholder="Apellido" bind:value={apellido}/>
					<input type="text" name="Correo" required placeholder="Correo" bind:value={correo}/>
					<input type="password" name="Contraseña" required placeholder="Contraseña" bind:value={contrasena}/>
					<input  class="boton" type="submit" value="Registrarse" />
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

	main{
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

	article{
		display: flex;
		align-items: center;
	}

	article .center-text {
		margin-left: 30%;
		margin-right: 30%;
	}

	
	h2{
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