<script setup>
import { Link } from "@inertiajs/vue3";
import TextInput from "./TextInput.vue";
import { ref } from "vue";

defineProps({
    items: {
        type: Array,
        required: true,
    },
});

const date = ref(new Date());
const currentDate = () => {
    const options = {
        weekday: "long",
        month: "long",
        day: "numeric",
        year: "numeric",
    };
    return date.value.toLocaleDateString("en-US", options);
};
</script>

<template>
    <div class="flex flex-col">
        <div
            class="flex items-center justify-between w-full navbar bg-base-100"
        >
            <div class="navbar-start">
                <div class="dropdown">
                    <div
                        tabindex="0"
                        role="button"
                        class="btn btn-ghost lg:hidden"
                    >
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            class="w-5 h-5"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                stroke-width="2"
                                d="M4 6h16M4 12h8m-8 6h16"
                            />
                        </svg>
                    </div>
                    <ul
                        tabindex="0"
                        class="menu bg-base-100 menu-sm dropdown-content mt-3 z-[1] p-2 shadow rounded-box w-52"
                    >
                        <li v-for="item in items" :key="item.id" class="">
                            <Link :href="item.link">{{ item.name }}</Link>
                        </li>
                    </ul>
                </div>
                <label
                    class="flex items-center border-none rounded-sm input-xs input input-ghost focus:color-primary"
                >
                    <TextInput
                        v-model="search"
                        type="text"
                        placeholder="Search"
                        class="p-0 text-base border-none input"
                    />
                    <Link href="#" type="submit">
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 16 16"
                            fill="currentColor"
                            class="w-4 h-4 opacity-70"
                        >
                            <path
                                fill-rule="evenodd"
                                d="M9.965 11.026a5 5 0 1 1 1.06-1.06l2.755 2.754a.75.75 0 1 1-1.06 1.06l-2.755-2.754ZM10.5 7a3.5 3.5 0 1 1-7 0 3.5 3.5 0 0 1 7 0Z"
                                clip-rule="evenodd"
                            />
                        </svg>
                    </Link>
                </label>
            </div>
            <div class="hidden navbar-center lg:flex">
                <ul
                    class="px-1 text-sm uppercase menu-xs menu-horizontal menu-title"
                >
                    <li
                        v-for="item in items"
                        :key="item.id"
                        class="px-2 py-1 tracking-wider duration-150 delay-100 rounded-sm hover:bg-indigo-50"
                        :class="item.current ? 'text-indigo-900' : ''"
                    >
                        <Link :href="item.link">{{ item.name }}</Link>
                    </li>
                </ul>
            </div>
            <div class="flex items-center gap-3 navbar-end">
                <Link
                    :href="route('login')"
                    class="px-2 py-1 text-xs font-bold text-white uppercase bg-indigo-900 rounded hover:bg-indigo-800"
                    >Log in</Link
                >
                <Link
                    href="#"
                    class="px-2 py-1 text-xs font-bold text-white uppercase bg-indigo-900 rounded hover:bg-indigo-800"
                    >Support Us</Link
                >
            </div>
        </div>
        <div class="flex flex-row items-center justify-between w-full navbar">
            <div class="basis-1/6 navbar-start">
                <!-- <p class="text-sm">Sunday, May 5, 2024</p> -->
                <div class="flex flex-col">
                    <p class="text-sm">Earth Time :</p>
                    <p class="text-sm">{{ currentDate() }}</p>
                </div>
            </div>
            <div class="items-center justify-center basis-1/2 navbar-center">
                <h1 class="text-4xl font-bold tracking-widest font-orbit">
                    The Observable Universe
                </h1>
            </div>
            <div class="items-center gap-3 basis-1/6 navbar-end">
                <span class="text-xs">Good Morning or Good Night</span>
            </div>
        </div>
    </div>
    <div class="flex flex-col gap-1">
        <div class="w-full border-b border-indigo-900"></div>
        <div class="w-full border-b border-indigo-900"></div>
    </div>
</template>
