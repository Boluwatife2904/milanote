<script setup lang="ts">
interface InputProps {
	name: string;
	id: string;
	type: string;
	placeholder?: string;
}

defineProps<InputProps>();
</script>

<template>
	<div class="base-input">
		<input :type="type" :name="name" :id="id" :placeholder="placeholder" class="base-input__element" />
	</div>
</template>

<style lang="scss" scoped>
.base-input {
	width: 100%;

	&__element {
		min-height: 4rem;
		width: 100%;
		border: none;
		padding: 0.8rem 1.6rem;
		border-radius: 1.2rem;
		background: var(--input-background);
		color: var(--primary-text);
		@include typeface(400, 1.4rem, 2.1rem);
	}

	&::placeholder {
		color: var(--primary-text);
	}
}
</style>
