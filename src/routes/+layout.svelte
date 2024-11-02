<script>
	import '../app.pcss';
</script>

<svelte:head>
	<title>Blood Pressure Calculator</title>
	<meta
		name="viewport"
		content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0"
	/>
	<link rel="icon" type="image/svg+xml" href="favicon.svg" />
	<script defer data-domain="bloodpressure.tbuser.dev" src="https://plausible.tbuser.dev/js/script.js"></script>
</svelte:head>

<div class="flex h-screen items-center justify-center bg-[#151518]">
	<slot></slot>
</div>
