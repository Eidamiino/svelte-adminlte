<script>
	/**
	 * @type {"button" | "reset" | "submit" | null | undefined}
	 */
	export let type = "button"
	/**
	 * @type {string | null}
	 */
	export let color = null
	/**
	 * @type {string | null}
	 */
	export let toggle = null

	export let xsmall = false
	export let small = false
	export let large = false
	export let borderless = false
	export let outlined = false
	export let social = false
	export let link = false
	export let disabled = false
	export let app = false
	export let squared = false

	let buttonClass

	$: buttonClass = "btn-" +
		(outlined && 'outline-' || '') +
		(color || 'default')
</script>

<button
	class:btn-app={app}
	class:btn-flat={borderless}
	class:btn-lg={large}
	class:btn-link={link}
	class:btn-sm={small}
	class:btn-social={social}
	class:btn-xs={xsmall}
	class:disabled
	class:squared
	{type}
	data-toggle={toggle || null}
	{disabled}
	{...$$restProps}
	class="btn btn-flat {buttonClass} {$$restProps.class || ''}"
	on:click
>
	<!-- note: the class attribute is after the {...$$restProps} on purpose -> to prevent static classes from being overriden -->
	<slot />
</button>

<style lang="scss">
	.squared {
		display: inline-flex;
		align-items: center;
		justify-content: center;

		width: 3rem;
		height: 3rem;
		padding: .1rem;

		&:hover {
			text-decoration: none
		}
	}
</style>
