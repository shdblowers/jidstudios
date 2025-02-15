<template>
    <div class="mt-16 mb-8 text-center">
        <h1 class="text-4xl font-bold">
            <slot name="title">Title</slot>
        </h1>
        <div v-if="$slots.desc">
            <p class="text-lg mt-4 text-slate-600">
                <slot name="desc">Some description goes here</slot>
            </p>
        </div>
    </div>
</template>