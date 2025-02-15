<script setup>
const links = [
    {
        title: "Home",
        path: '/'
    },
    // {
    //     title: "What we do",
    //     path: "/services",
    // },
    // {
    //     title: "About us",
    //     path: "/about",
    // },
    // {
    //     title: "Portfolio",
    //     path: "/portfolio",
    // },
    // {
    //     title: "Publications",
    //     path: "/publications",
    // },
    {
        title: "Contact",
        path: "/contact",
    },
];
</script>

<template>
    <Container>
        <header class="flex flex-col lg:flex-row justify-between items-center my-5">
            <div class="flex w-full lg:w-auto items-center justify-between">
                <NuxtLink to="/" class="text-lg">
                    <span>j</span>
                    <span class="font-bold">ID</span>
                    <span> Studios</span>
                </NuxtLink>
            </div>
            <nav>
                <ul class="flex flex-row">
                    <li v-for="link in links">
                        <span class="flex px-3">
                            <NuxtLink v-bind:to="link.path">{{ link.title }}</NuxtLink>
                        </span>
                    </li>
                </ul>
            </nav>
        </header>
    </Container>
</template>