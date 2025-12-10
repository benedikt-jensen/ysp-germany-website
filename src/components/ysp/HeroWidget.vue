<script setup>
const baseUrl = import.meta.env.BASE_URL;
</script>

<template>
    <div
        id="hero"
        class="flex flex-col pt-6 px-6 lg:px-20 overflow-hidden"
        :style="`background-image: url(${baseUrl}ysp/images/photos/landing_img_berlin_homeless.jpg);`"
        style="background-size: cover; background-position: 25% 45%; height:800px; clip-path: ellipse(150% 87% at 93% 13%);">
        <div class="mx-6 md:mx-20 mt-0 md:mt-6">
            <h1 class="text-6xl text-shadow leading-tight">
                <span class="font-light block">YSP Germany</span>
                Youth and Students for Peace
            </h1>
            <Button label="Sei dabei!" as="router-link" to="/events" rounded class="!text-xl mt-8 !px-4"></Button>
        </div>
    </div>
</template>
