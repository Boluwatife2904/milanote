<script setup lang="ts"></script>

<template>
    <div class="hero">
        <div class="hero-content">
            <h1 class="hero-content__title krylon-font"><span class="block">Seamlessly Organize</span></h1>
            <h1 class="hero-content__title krylon-font"><span class="block">Ideas and Projects</span></h1>
            <p class="hero-content__description">Your ultimate solution for effortless visual idea organization and project management.</p>
            <form class="hero-content__form flex">
                <BaseInput name="email" id="email" type="email" placeholder="Enter your email" />
                <BaseButton variant="primary">Join Waitlist</BaseButton>
            </form>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.hero {
    position: fixed;
    top: 23%;
    left: 50%;
    transform: translate(-50%, -23%);

    &-content {
        max-width: 53.8rem;
        text-align: center;

        &__title {
            @include typeface(400, 6.4rem, 6.4rem);
            overflow: hidden;

            &:not(:first-child) {
                margin-bottom: 1.6rem;
            }
        }

        &__description {
            max-width: 42.6rem;
            @include typeface(400, 1.6rem, 2.4rem);
            margin: 0 auto 2.4rem;
        }

        &__form {
            max-width: 33rem;
            margin: 0 auto;
            gap: 0.8rem;
        }
    }
}
</style>
