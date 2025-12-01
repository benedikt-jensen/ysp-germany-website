<script setup lang="ts">
import FeaturesWidget from '@/components/landing/FeaturesWidget.vue';
import FooterWidget from '@/components/landing/FooterWidget.vue';
import HeroWidget from '@/components/ysp/HeroWidget.vue';
import HighlightsWidget from '@/components/landing/HighlightsWidget.vue';
import PricingWidget from '@/components/landing/PricingWidget.vue';
import TopbarWidget from '@/components/ysp/TopbarWidget.vue';
import {ref} from "vue";

const galleriaResponsiveOptions = ref([
    {
        breakpoint: '1024px',
        numVisible: 5
    },
    {
        breakpoint: '960px',
        numVisible: 4
    },
    {
        breakpoint: '768px',
        numVisible: 3
    },
    {
        breakpoint: '560px',
        numVisible: 1
    }
]);

const images = [
    {
        itemImageSrc: '/ysp/images/photos/IMG-20250729-WA0022.jpg',
        thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria1s.jpg',
        alt: 'Description for Image 1',
        title: 'Title 1'
    },
    {
        itemImageSrc: '/ysp/images/photos/IMG-20250729-WA0024.jpg',
        thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria2s.jpg',
        alt: 'Description for Image 2',
        title: 'Title 2'
    },
    {
        itemImageSrc: '/ysp/images/photos/IMG-20250729-WA0020.jpg',
        thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria3s.jpg',
        alt: 'Description for Image 3',
        title: 'Title 3'
    },
];

const carouselResponsiveOptions = ref([
    {
        breakpoint: '560px',
        numVisible: 1,
        numScroll: 1
    }
]);
</script>

<style>

</style>

<template>
    <div v-for="i in [1,2,3]" class="card m-0 lg:m-5" style="min-height:200px;">

        <div class="flex flex-col lg:flex-row m-0 lg:m-2">
            <Carousel class="-mx-5 md:mx-0" style="flex: 0 0 50%;" :value="images" :numVisible="1" :numScroll="1" :responsiveOptions="carouselResponsiveOptions">
                <template #item="slotProps">
                    <div class="border border-surface-200 dark:border-surface-700 rounded lg:m-2 p-2 lg:p-4">
                        <div class="relative mx-auto">
                            <img :src="slotProps.data.itemImageSrc" :alt="slotProps.data.name" style="max-height: 340px; object-fit: cover;" class="w-full rounded"/>
                        </div>
                    </div>
                </template>
            </Carousel>
            <div>
                <h4>Geschenke für Obdachlose</h4>
                <p>
                    Wir haben zusammen Wraps zubereitet und diese an Obdachlose in Berlin verteilt. Es war eine bereichernde Erfahrung, die uns gezeigt hat, wie wichtig es ist, Mitgefühl und Unterstützung in unserer Gemeinschaft zu fördern.
                </p>
                <p>
                    Diese Aktion war die zweite dieser Art, und wir haben vor, sie regelmäßig zu wiederholen, um weiterhin einen positiven Einfluss auf das Leben der Bedürftigen zu haben.
                </p>
            </div>
        </div>

    </div>
    <div class="end-of-page"></div>
</template>
