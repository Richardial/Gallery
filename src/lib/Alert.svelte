<script>
	export let success = false;

	let alertState = 'failure';
	let alertText = '';
	let alertText2 = '';

	if (success) {
		alertState = 'success';
		alertText = 'Usuario creado exitosamente';
	} else {
		alertState = 'failure';
		alertText = 'Error';
		alertText2 = 'Credenciales incorrectas';
	}
</script>

	<div class="alert {alertState}">
		<p>{alertText}</p>
		<p class="mini">{alertText2}</p>
	</div>

<style>
	.alert {
		position: absolute;
		display: flex;
		flex-direction: column;
		box-sizing: border-box;

		top: 30px;
		right: 0px;
		width: 280px;
		height: auto;
		max-height: calc(100% - 30px);
		transition: right 0.3s ease-in-out;
		border-style: solid;
		border-width: 2px;
		margin-top: 45px;
		z-index: 10;
		align-items: center;
		justify-content: center;
		text-align: center;
		-webkit-animation-name: alertAnimation;
		-webkit-animation-duration: 0.7s;
		animation-name: alertAnimation;
		animation-duration: 0.7s;
		padding: 12px;
	}

	.failure {
		border-color: #f85050;
		background-color: #8f3f3f;
	}

	.success {
		border-color: #72f850;
		background-color: #3f8f50;
	}

	p {
		margin: 0;

		color: #f7f1f1;
		font-size: 20px;
	}

	.mini {
		font-size: 15px;
	}

	@keyframes alertAnimation {
		from {
			right: -280px;
		}
		to {
			right: 0px;
		}
	}

	@-webkit-keyframes alertAnimation {
		from {
			right: -280px;
		}
		to {
			right: 0px;
		}
	}
</style>
