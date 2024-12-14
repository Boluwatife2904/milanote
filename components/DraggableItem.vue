<script setup lang="ts">
interface Props {
	position: {
		top?: string;
		left?: string;
		right?: string;
		bottom?: string;
	};
}

defineProps<Props>();

const draggable = ref<HTMLDivElement | null>(null);

const active = ref(false);
const currentX = ref<null | number>(null);
const currentY = ref<null | number>(null);
const initialX = ref<null | number>(null);
const initialY = ref<null | number>(null);
const xOffset = ref(0);
const yOffset = ref(0);

const drag = (e: Event) => {
	if (active.value) {
		e.preventDefault();

		if (e.type === "touchmove") {
			currentX.value = e.touches[0].clientX - initialX.value;
			currentY.value = e.touches[0].clientY - initialY.value;
		} else {
			currentX.value = e.clientX - initialX.value;
			currentY.value = e.clientY - initialY.value;
		}

		xOffset.value = currentX.value;
		yOffset.value = currentY.value;

		setTranslate(currentX.value, currentY.value, draggable.value);
	}
};
const startDragging = (e: Event) => {
	console.log("We got to start dragging");
	if (e.type === "touchstart") {
		initialX.value = e.touches[0].clientX - xOffset.value;
		initialY.value = e.touches[0].clientY - yOffset.value;
	} else {
		initialX.value = e.clientX - xOffset.value;
		initialY.value = e.clientY - yOffset.value;
	}
	console.log(e.target);
	if (e.target === draggable.value) active.value = true;
};

const stopDragging = () => {
	initialX.value = currentX.value;
	initialY.value = currentY.value;

	active.value = false;
};

const setTranslate = (xPos: number, yPos: number, el: HTMLDivElement | null) => {
	if (el) el.style.transform = "translate3d(" + xPos + "px, " + yPos + "px, 0)";
};

onMounted(() => {
	draggable.value?.addEventListener("touchstart", startDragging, false);
	draggable.value?.addEventListener("touchend", stopDragging, false);
	draggable.value?.addEventListener("touchmove", drag, false);

	draggable.value?.addEventListener("mousedown", startDragging, false);
	draggable.value?.addEventListener("mouseup", stopDragging, false);
	draggable.value?.addEventListener("mousemove", drag, false);
});
</script>

<template>
	<div ref="draggable" class="draggable-item" :style="{ ...position }">
		<slot></slot>
	</div>
</template>

<style lang="scss" scoped>
.draggable-item {
	position: fixed;
	will-change: transform;
	transition: all 0.3s transform;
	max-width: max-content;
	cursor: grab;
	z-index: 100
}
</style>
