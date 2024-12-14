<script lang="ts" setup>
import gsap from "gsap";
const ideas = [
	{
		position: { top: "42%", left: "10%" },
		idea: { background: "#4F55A0", image: "sneakers.png", slug: "/illustration.png", title: "illustration", boards: 1, files: 2, font: "fredericka", colors: { heading: "#fff", paragraph: "#D7D7D7" } },
	},
	{
		position: { top: "calc(42% + 6.8rem)", left: "calc(10% + 7.9rem)" },
		idea: { background: "#F7D469", image: "vr.png", slug: "/videos.png", title: "videos", boards: 1, files: 2, font: "manrope", colors: { heading: "#090909", paragraph: "#090909" } },
	},
	{
		position: { top: "42%", right: "calc(10% + 6.8rem)" },
		idea: { background: "#D42E2C", image: "sneakers.png", slug: "/art-direction.png", title: "art direction", boards: 0, files: 20, font: "fredericka", colors: { heading: "#fff", paragraph: "#fff" } },
	},
	{
		position: { top: "calc(42% + 6.8rem)", right: "10%" },
		idea: { background: "#090909", image: "vr.png", slug: "/moodboard.png", title: "moodboard", boards: 1, files: 2, font: "manrope", colors: { heading: "#fff", paragraph: "#C8C8C8" } },
	},
];

onMounted(() => {
	gsap.set("body", { visibility: "visible" });
	const timeline = gsap.timeline({ paused: true, defaults: { duration: 0.75 } });
	timeline
		// .from(".header", { opacity: 0 })
		.from(".hero-content__title span", { yPercent: 100, opacity: 0.6, duration: 1, stagger: 0.1, ease: "power2.inOut" }, "<")
		.from(".hero-content__description", { y: 30, opacity: 0 }, "<80%")
		.from(".hero-content__form", { y: 30, opacity: 0 }, "<25%")
		.from(".idea-card", { y: 50, opacity: 0, stagger: 0.1 }, "<75%")
		.to(".home__image--before", { width: 0, duration: 1.5, ease: "power2.inOut" }, "<")
		.to(".home__image--after", { width: 0, duration: 1.5, ease: "power2.inOut" }, "<25%")
		.from(".home__image img", { scale: 2, duration: 2.5 }, 1.5);
	timeline.play();
});
</script>

<template>
	<main class="home">
		<TheHeader />
		<HomeHero />
		<DraggableItem v-for="idea in ideas" :key="idea.idea.title" :position="idea.position">
			<IdeaCard :idea="idea.idea" />
		</DraggableItem>
		<div class="home__image">
			<img src="/hero.svg" />
			<div class="home__image--before"></div>
			<div class="home__image--after"></div>
		</div>
	</main>
</template>

<style lang="scss" scoped>
.home__image {
	position: fixed;
	left: 50%;
	transform: translateX(-50%);
	bottom: 0;
	// min-height: 23.7rem;
	width: 100%;
	max-width: 119.1rem;
	margin: 0 auto;
	overflow: hidden;

	&--before,
	&--after {
		content: "";
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;
		width: 100%;
	}

	&--before {
		z-index: 3;
		background-color: var(--body-background);
	}

	&--after {
		background-color: #fff;
		z-index: 2;
	}

	img {
		height: auto;
		width: 100%;
		object-fit: contain;
	}
}
</style>
