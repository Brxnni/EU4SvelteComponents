<script>

	export let src;
	export let alt = "";
	export let ariaHidden = true;

</script>

<style>

	div {
		display: inline-block;
	}
	
	img {
		margin-bottom: -6px;
		height: 1.2em;

		/* Disable dragging the image */
		user-select: none;
		-moz-user-select: none;
		-webkit-user-drag: none;
		-webkit-user-select: none;
		-ms-user-select: none;
	}

</style>

<div class="inlineImage">
	<img {src} {alt} aria-hidden={ariaHidden}>
</div>
