<script setup>
import FloatingConfigurator from "@/components/FloatingConfigurator.vue";

function smoothScroll(id) {
    document.body.click();
    const element = document.getElementById(id);
    if (element) {
        element.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    }
}

function isActiveRoute(route) {
    return route === useRouter().currentRoute.value.path;
}

function linkClass(route) {
    return ['px-8 py-4 text-surface-900 dark:text-surface-0 font-medium text-xl', { 'bg-surface-200 dark:bg-surface-700': isActiveRoute(route) }];
}

import { useRouter } from 'vue-router';

const router = useRouter();

router.afterEach(() => {
    // If your menu closes on body click, keep this.
    // Otherwise call a direct close method (see other options).
    document.body.click();
});
</script>

<template>
    <a class="flex items-center" href="#">
        <img src="/ysp/images/logo.png" alt="logo" width="50px" height="50px" style="margin-right:20px;">
        <span class="text-surface-900 dark:text-surface-0 font-medium text-2xl leading-normal mr-20">YSP</span>
    </a>
    <Button
        class="lg:!hidden"
        text
        severity="secondary"
        rounded
        v-styleclass="{ selector: '@next', enterFromClass: 'hidden', enterActiveClass: 'animate-scalein', leaveToClass: 'hidden', leaveActiveClass: 'animate-fadeout', hideOnOutsideClick: true }"
    >
        <i class="pi pi-bars !text-2xl"></i>
    </Button>
    <div class="items-center bg-surface-0 dark:bg-surface-900 grow justify-between hidden  lg:flex absolute lg:static w-full left-0 top-full px-12 lg:px-0 z-20 rounded-border">
        <ul class="list-none p-0 m-0 flex lg:items-center select-none flex-col lg:flex-row cursor-pointer my-5 lg:my-0 gap-0 gap-y-8">
            <li>
                <router-link to="/about" :class="linkClass('/about')">
                    <span>Über uns</span>
                </router-link>
            </li>
            <li>
                <router-link to="/reports" :class="linkClass('/reports')">
                    <span>Berichte</span>
                </router-link>
            </li>
            <li>
                <router-link to="/events" :class="linkClass('/events')">
                    <span>Aktuelles</span>
                </router-link>
            </li>
            <li>
                <router-link to="/" :class="linkClass('/')">
                    <span>Admin</span>
                </router-link>
            </li>
        </ul>
    </div>
    <FloatingConfigurator style="right:120px; top: 20px; z-index: 300;"/>
</template>
