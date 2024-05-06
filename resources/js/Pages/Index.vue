<script setup>
import NavBar from "@/Components/NavBar.vue";
import { Head, Link } from "@inertiajs/vue3";

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

const items = [
    {
        name: "Solar System",
        link: "/solar-system",
        current: true,
        id: 1,
    },
    {
        name: "Milky Way",
        link: "/milky-way",
        current: false,
        id: 2,
    },
    {
        name: "Universal",
        link: "/universal",
        current: false,
        id: 3,
    },
    {
        name: "Andromeda",
        link: "/andromeda",
        current: false,
        id: 4,
    },
];

function handleImageError() {
    document.getElementById("screenshot-container")?.classList.add("!hidden");
    document.getElementById("docs-card")?.classList.add("!row-span-1");
    document.getElementById("docs-card-content")?.classList.add("!flex-row");
    document.getElementById("background")?.classList.add("!hidden");
}
</script>

<template>
    <Head title="The Observable Universe" />
    <div class="default-layout">
        <div class="">
            <header class="px-4 mx-auto max-w-7xl sm:px-6 lg:px-8">
                <NavBar :items="items" />
            </header>

            <main class="mt-6"></main>

            <footer
                class="py-16 text-sm text-center text-black dark:text-white/70"
            ></footer>
        </div>
    </div>
</template>

<style scoped>
.default-layout {
    font-family: "Exo 2", sans-serif;
}
</style>
