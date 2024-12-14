<script setup lang="ts"></script>

<template>
	<header class="header flex items-center content-space-between">
		<div class="header--left">
			<span class="header__logo">Name</span>
		</div>
		<div class="header--right flex items-center">
			<BaseButton variant="none">Login</BaseButton>
			<BaseButton variant="primary">Join Waitlist</BaseButton>
		</div>
	</header>
</template>

<style lang="scss" scoped>
.header {
	max-width: 129.1rem;
	margin: 0 auto;
	padding: 4rem 4rem 0;

	&--right {
		gap: 2.4rem;
	}

	&__logo {
		@include typeface(400, 1.6rem, 2.4rem);
	}
}
</style>
