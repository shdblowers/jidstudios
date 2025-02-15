<template>
    <form @submit.prevent="submitForm">
        <input type="checkbox" class="hidden" style="display: none" name="botcheck" />
        <input type="text" name="name" v-model="form.name" placeholder="Full Name"
            class="w-full px-4 py-3 border-2 placeholder:text-gray-800 rounded-md outline-none focus:ring-4 border-gray-300 focus:border-gray-600 ring-gray-100" />
        <input type="email" name="email" v-model="form.email" placeholder="Email Address"
            class="w-full px-4 py-3 border-2 placeholder:text-gray-800 rounded-md outline-none focus:ring-4 border-gray-300 focus:border-gray-600 ring-gray-100" />
        <textarea name="message" v-model="form.message" placeholder="Your Message"
            class="w-full px-4 py-3 border-2 placeholder:text-gray-800 rounded-md outline-none h-36 focus:ring-4 border-gray-300 focus:border-gray-600 ring-gray-100"></textarea>
        <button type="submit" class="bg-black text-white w-full rounded px-6 py-3 my-5 cursor-pointer">Send
            Message</button>
    </form>
</template>

<script setup>
const form = ref({
    access_key: "xxxxxxxxxxxxxxxxxxxxxxxxxx",
    subject: "New Submission from Web3Forms",
    name: "",
    email: "",
    message: "",
});

const result = ref("");
const status = ref("");

const submitForm = async () => {
    try {
        status.value = "loading";
        const response = await $fetch("https://api.web3forms.com/submit", {
            method: "POST",
            body: form.value,
        });
        console.log(response);
        result.value = response.message;
        if (response.status === 200) {
            status.value = "success";
        } else {
            console.log(response); // Log for debugging, can be removed
            status.value = "error";
        }
    } catch (error) {
        console.log(error); // Log for debugging, can be removed
        status.value = "error";
        result.value = "Something went wrong!";
    } finally {
        // Reset form after submission
        form.value.name = "";
        form.value.email = "";
        form.value.message = "";

        // Clear result and status after 5 seconds
        setTimeout(() => {
            result.value = "";
            status.value = "";
        }, 5000);
    }
};
</script>