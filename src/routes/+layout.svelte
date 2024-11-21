<script>
import Header from '$lib/Header.svelte';

</script>
<head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin=''>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400..900&display=swap" rel="stylesheet">
</head>
<body>
	<Header/>
	<slot />
</body>

<style>
	
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-family: 'Cinzel', serif;
		font-optical-sizing: auto;
		font-weight: 600;
		font-style: regular;
	}

	body {
		background-color: #332e2e;
		box-sizing: border-box;
		color: rgb(255, 255, 255);
		overflow-x: hidden;
	}
</style>
