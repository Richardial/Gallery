<script>

</script>


	<main>
		<section>
			<h2>Verano 2024</h2>
			<article class="galeria">
				<img id="Img1" src="Imagen 1.jpg" alt="" />
				<img id="Img2" src="Imagen 2.jpg" alt="" />
				<img id="Img3" src="Imagen 3.jpg" alt="" />
			</article>
			<article>
				<p class="center-text">
					"Cada imagen es un susurro del bosque, un recordatorio de que en la naturaleza encontramos
					la paz que el alma busca y la belleza que los ojos anhelan."
				</p>
			</article>
		</section>
	</main>
	<main class="gallery-2">
		<section>
			<h2>Mejores Trabajos</h2>
			<article class="galeria-otros">
				<img src="Imagen 4.jpg" alt="" />
				<img src="Imagen 5.jpg" alt="" />
				<img src="Imagen 6.jpg" alt="" />
				<img src="Imagen 7.jpg" alt="" />
				<img src="Imagen 8.jpg" alt="" />
				<img src="Imagen 9.jpg" alt="" />
				<img src="Imagen 10.jpg" alt="" />
				<img src="Imagen 11.jpg" alt="" />
				<img src="Imagen 13.jpg" alt="" />
				<img src="Imagen 12.jpg" alt="" />
				<img src="Imagen 14.jpg" alt="" />
				<img src="Imagen 15.jpg" alt="" />
				<img src="Imagen 16.jpg" alt="" />
				<img src="Imagen 17.jpg" alt="" />
				<img src="Imagen 18.jpg" alt="" />
				<img src="Imagen 19.jpg" alt="" />
				<img src="Imagen 20.jpg" alt="" />
				<img src="Imagen 21.jpg" alt="" />
				<img src="Imagen 17.jpg" alt="" />
				<img src="Imagen 22.jpg" alt="" />
			</article>
		</section>
	</main>
	<main class="idk">
		<section>
			<h2>Premiaciones</h2>
			<article class="">
				<img class="premio" src="Premio.png" alt="">
			</article>
		</section>
	</main>

<style>
	main {
		width: 100%;
		height: 88vh;
	}

	article{
		display: flex;
		justify-content: center;
		/* align-items: center; */
	}
	
	.gallery-2, .idk{
		overflow-x: hidden;
		height: 100vh;
	}

	.premio{
		width: 40%;
		height: 50%;
		object-fit: cover;
	}

	h2 {
		margin: 30px;
	}
	.galeria img {
		width: 15%;
		box-shadow:
			0 4px 8px 0 rgba(0, 0, 0, 0.2),
			0 6px 20px 0 rgba(0, 0, 0, 0.19);
		transition-duration: 0.5s;
	}

	.galeria img:hover , .galeria-otros img:hover {
		transform: scale(1.2);
		transition-duration: 0.5s;
	}

	.galeria-otros{
		display: flex;
		flex-wrap: wrap;
		gap: 0rem;
		width: 100%;
		margin-top: 50px;
	}

	
	.galeria-otros img{
		width: 10%;
	}

	.center-text {
		text-align: center;
		margin-top: 30px;
	}
	article .center-text {
		margin-left: 30%;
		margin-right: 30%;
	}
	.galeria {
		display: flex;
		justify-content: center;
	}
	.galeria img {
		margin-right: 20px;
		margin-left: 20px;
	}

</style>
