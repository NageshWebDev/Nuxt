<template>
    <nav
        class="z-50 fixed w-full flex flex-col space-y-5 sm:space-y-0 sm:flex-row justify-between items-center py-5 px-10 bg-gray-100 shadow-sm border-b-[1px]">
        <main><a class="text-2xl" v-on:click="onClickHandler('logo')" href="#">LOGO</a></main>
        <ul class="flex justify-evenly space-x-10 bg-gray-300 p-2 rounded-lg w-[300px]">
            <li><a v-on:click="onClickHandler('home')" class="hover:border-b-2 border-gray-400"
                    :class="{ 'border-b-2 border-gray-400': homeSelected }">Home</a></li>
            <li><a v-on:click="onClickHandler('about')" class="hover:border-b-2 border-gray-400"
                    :class="{ 'border-b-2 border-gray-400': aboutSelected }">About</a></li>
            <li><a v-on:click="onClickHandler('login')" class="hover:border-b-2 border-gray-400"
                    :class="{ 'border-b-2 border-gray-400': loginSelected }">Login</a>
            </li>
        </ul>
    </nav>
</template>

<script setup>
const homeSelected = ref(false)
const aboutSelected = ref(false)
const loginSelected = ref(false)
const logoSelected = ref(false)

function onClickHandler(type) {
    // Ref to store the element to scroll to
    const scrollToElement = ref(null);

    // Function to scroll to the element
    const scrollToSection = (sectionId) => {
        const element = document.querySelector(sectionId);
        const offset = 50;
        if (element) {
            scrollToElement.value = element;
            console.log(offset)
            element.scrollIntoView({ behavior: 'smooth',block: 'start', inline: 'nearest', offsetTop: offset });
        }
    };

    switch (type) {
        case 'home':
            homeSelected.value = true;
            aboutSelected.value = false;
            loginSelected.value = false;
            logoSelected.value = false;
            scrollToSection('#home')
            break;

        case 'about':
            homeSelected.value = false;
            aboutSelected.value = true;
            loginSelected.value = false;
            logoSelected.value = false;
            scrollToSection('#about')
            break;

        case 'login':
            homeSelected.value = false;
            aboutSelected.value = false;
            loginSelected.value = true;
            logoSelected.value = false;
            scrollToSection('#login')
            break;

        case 'logo':
            homeSelected.value = false;
            aboutSelected.value = false;
            loginSelected.value = false;
            logoSelected.value = true;
            break;

        default:
            break;
    }
}
</script>