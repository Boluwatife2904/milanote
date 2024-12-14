<script setup lang="ts">
interface Idea {
	font: string;
	title: string;
	files: number;
	boards: number;
	slug: string;
	image: string;
	background: string;
	colors: {
		heading: string;
		paragraph: string;
	};
}

interface Props {
	idea: Idea;
}

defineProps<Props>();
</script>

<template>
	<div class="idea-card flex items-center" :style="{ background: idea.background }">
		<div class="idea-card--left">
			<img :src="idea.image" alt="" class="idea-card__image" />
		</div>
		<div class="idea--card--right flex flex-column">
			<h4 class="idea-card--title" :class="`${idea.font}-font`" :style="{ color: idea.colors.heading }">{{ idea.title }}</h4>
			<p class="idea-card__paragraph" :style="{ color: idea.colors.paragraph }">
				<span v-if="idea.boards > 0"> {{ idea.boards }} board<span v-if="idea.boards > 1">s</span>, &nbsp;</span>
				<span>{{ idea.files }} files</span>
			</p>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.idea-card {
	gap: 0.6rem;
	padding: 0.4rem 0.8rem 0.4rem 0.4rem;
	border-radius: 0.8rem;
	max-width: max-content;
	pointer-events: none;
	-webkit-user-select: none;
	-ms-user-select: none;
	user-select: none;

	&--left {
		height: 3.2rem;
		width: 3.2rem;
	}

	&--right {
		gap: 0.6rem;
	}

	&__image {
		height: 100%;
		width: 100%;
		object-fit: cover;
	}

	.fredericka-font {
		@include typeface(400, 1.6rem, 1.6rem);
	}

	.manrope-font {
		@include typeface(400, 1.4rem, 1.4rem);
	}

	&__paragraph {
		@include typeface(400, 1rem, 1.5rem);
	}
}
</style>
