<style>

	:root {
		--border-container-radius: 45px;
	}

	div.bordercontainer {
		position: relative;

		/* Hide background behind border.
		   I could do this using a custom path, but this pretty well. */
		border-radius: 60px;
		
		/* Compensate for border, but the full border is gigantic so just a fraction of it */
		padding: calc(var(--border-container-radius) * 0.9);
	}

	div.border {
		position: absolute;
		top: 0;
		right: 0;
		left: 0;
		bottom: 0;

		border: var(--border-container-radius) solid rgba(0,0,0,0);
		border-image: url(/other/gold_border.png) 45/var(--border-container-radius) repeat;
		/* Quick solution to make edges less sharp */
		filter: blur(0.4px);

		/* Same width without border */
		width: calc(100% - 2*var(--border-container-radius));
		height: calc(100% - 2*var(--border-container-radius));
		
		/* Make sure hovering and clicking goes through the element */
		pointer-events: none;
	}

</style>

<div class="bordercontainer">
	<div class="border"></div>
	<div class="slot"><slot /></div>
</div>