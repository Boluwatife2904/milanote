<script setup lang="ts">
interface Props {
	variant?: string;
}

const { variant = "none" } = defineProps<Props>();

const buttonClasses = computed(() => {
	return ["variant"].map((buttonProp) => {
		if (buttonProp === "variant") return `button--variant-${variant}`;
	});
});
</script>

<template>
	<button :class="buttonClasses">
		<slot />
	</button>
</template>

<style lang="scss" scoped>
.button {
	&--none {
		@include typeface(400, 1.6rem, 2.4rem);
		color: var(--primary-text);
	}

	&--variant-primary {
		height: 4rem;
		// padding: 1.5rem 0.8rem;
		background-color: var(--primary-text);
		color: #fff;
		min-width: 12.2rem;
		border-radius: 1.2rem;
		@include typeface(400, 1.4rem, 1.4rem);
	}
}
</style>
