<script>

	export let onClick = () => {};

</script>

<style>

	:root {
		--size-multiplier: 0.8;
		--height: 58px;
		--center-width: 139px;
		--end-width: 29px;
	}

	/* Prevent selecting button text */
	* { user-select: none; }

	/* Inline */
	div {
		display: inline-block;
		height: calc(var(--height) * var(--size-multiplier));
		max-width: 80% !important;

		/* Make sure backgrounds work when bigger */
		background-repeat: no-repeat;
		background-size: 100% 100%;

		white-space: nowrap;
	}

	div.button {
		height: calc(var(--height) * var(--size-multiplier));
	}

	div.beginning {
		width: calc(var(--end-width) * var(--size-multiplier));
		height: 100%;
	}

	div.end {
		width: calc(var(--end-width) * var(--size-multiplier));
		height: 100%;
		transform: scaleX(-1);
	}

	div.middle {
		/* Make sure its wide enough for text */
		width: fit-content;
		/* Full height */
		height: 100%;
		
		/* This makes it so that the div doesn't go down when <span> is added */
		vertical-align: top;
		text-align: center;
		
		/* Make sure background div is under the text */
		z-index: 0;

		/* Fix Mytserious 4px gap between images (caused by whitespace + inline-block) */
		margin-left: -8px;
		margin-right: -8px;

		/* Repeat background (almost unnoticable, need to improve on that) */
		background-repeat: repeat-x;
		background-size: calc(var(--center-width) * var(--size-multiplier)) calc(var(--height) * var(--size-multiplier));
	}
	
	/* Different images with normal and on hover */
	div div.beginning { 		background-image: url(/button/button_end_2.png); }
	div div.middle { 			background-image: url(/button/button_center_2.png); }
	div div.end { 				background-image: url(/button/button_end_2.png); }

	div:hover div { filter: brightness(120%); }

	/* Change cursor on hover for better ✨ UX ✨ */
	div:hover {
		cursor: pointer;
	}

	span {
		/* Align exactly in the center */
		display: block;
		margin-top: 0.65em;
		line-height: 1em;
		
		/* Min-width is (), gets bigger with content */
		width: max(calc(
			calc(
				(var(--height) + 2 * var(--end-width)) * var(--size-multiplier)
			)
		), fit-content);
		max-width: calc(100%);
		
		padding: 0 calc(25px * var(--size-multiplier)) 0 calc(25px * var(--size-multiplier));

		/* Reset font-size from 0 to normal size */
		font-size: calc(1em * var(--size-multiplier));

		/* Force into one line */
		text-overflow: ellipsis;
		overflow: hidden;
		white-space: nowrap;
	}

</style>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="button" on:click={onClick}>

	<div class="beginning"></div>
	<div class="middle"><span><slot/></span></div>
	<div class="end"></div>

</div>