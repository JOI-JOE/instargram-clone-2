<script setup>
import {ref} from 'vue';
import {Link} from '@inertiajs/vue3';

import Magnify from 'vue-material-design-icons/Magnify.vue';
import HeartOutline from 'vue-material-design-icons/HeartOutline.vue';
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';
import AccountPlusOutline from 'vue-material-design-icons/AccountPlusOutline.vue'
import HomeOutline from "vue-material-design-icons/HomeOutline.vue";
import Compass from "vue-material-design-icons/Compass.vue";
import SendOutline from "vue-material-design-icons/SendOutline.vue";
import Plus from 'vue-material-design-icons/Plus.vue';

import MenuItem from "@/Components/MenuItem.vue";
import CreatePostOverlay from "@/Components/CreatePostOverlay.vue";

let showCreatePost = ref(false);
</script>

<template>
    <div id="MainLayout" class="w-full h-screen">
        <div v-if="$page.url === '/'" id="TopNavHome" class="fixed z-30 md:hidden block w-full bg-white h-[61px] border-b border-b-gray-300">
            <div class="flex items-center justify-between h-full">

                <Link href="/">
                    <img class="w-[105px] ml-6 cursor-pointer" src="/insta-logo.png" alt="">
                </Link>

                <div class="flex items-center w-[50%]">
                    <div class="flex items-center w-full bg-gray-100 rounded-lg">
                        <Magnify class="pl-4" fillColor="#8E8E8E" :size="27" />
                        <input
                            type="text"
                            placeholder="Search"
                            class="bg-transparent w-full placeholder-[#8E8E8E]
                            border-0
                            ring-0
                            focus:ring-0
                            "
                        >
                    </div>

                    <HeartOutline class="pl-4 pr-3" fillColor="#000000" :size="27"/>
                </div>
            </div>
        </div>

        <!-- Top Nav User -->
        <div
            v-if="$page.url !== '/'"
            id="TopNavUser"
            class="md:hidden fixed flex items-center justify-between z-30 w-full bg-white h-[61px] border-b border-b-gray-300"
        >
            <Link href="/" class="px-4">
                <ChevronLeft :size="30" class="cursor-pointer"/>
            </Link>
            <div class="font-extrabold text-lg">Name Here</div>
            <AccountPlusOutline :size="30" class="cursor-pointer px-4"/>
        </div>

        <div id="SideNav" class="fixed h-full bg-white xl:w-[280px] w-[80px] md:block hidden border-r border-r-gray-300">

            <Link href="/">
                <img src="/insta-logo-small.png" alt="" class="xl:hidden block w-[25px] mt-10 ml-[25px] mb-10 cursor-pointer">
                <img src="/insta-logo.png" alt="" class="xl:block hidden w-[120px] mt-10 ml-6 mb-10 cursor-pointer">
            </Link>

            <div class="px-3">
                <Link href="/">
                    <MenuItem iconString="Home" class="mb-4" />
                </Link>
                    <MenuItem iconString="Search" class="mb-4" />
                    <MenuItem iconString="Explore" class="mb-4" />
                    <MenuItem iconString="Messages" class="mb-4" />
                    <MenuItem iconString="Notifications" class="mb-4" />
                    <MenuItem @click="$event => showCreatePost = true" iconString="Create" class="mb-4"/>
                    <Link href="/">
                        <MenuItem iconString="Profile" class="mb-4" />
                    </Link>

            </div>
            <Link href="/" class="absolute bottom-0 px-3 w-full">
                <MenuItem iconString="Log out" class="mb-4" />
            </Link>
        </div>

        <div class="flex lg:justify-between bg-white h-full w-[100%-280px] xl:pl-[280px] lg:pl-[100px] overflow-auto">
            <div
                class="mx-auto md:pt-6 pt-20"
                :class="$page.url === '/' ? 'lg:w-8/12 w-full' : 'max-w-[1200px]'"
            >
                <main>
                    <slot/>
                </main>
            </div>

            <div v-if="$page.url === '/'" id="SuggestionSection" class="lg:w-4/12 lg:block hidden text-black mt-10">
                <Link href="/" class="flex items-center justify-between max-w-[300px]">
                    <div class="flex items-center">
                        <img class="rounded-full z-10 w-[58px]" src="https://picsum.photos/id/50/300/320" alt="">
                        <div class="pl-4">
                            <div class="text-black font-extrabold">Name Here</div>
                            <div class="text-gray-500 text-extrabold text-sm">Name Here</div>
                        </div>
                    </div>
                    <button class="text-blue-500 hover:text-gray-900 text-xs font-extrabold">
                        Switch
                    </button>
                </Link>

                <div class="max-w-[300px] flex items-center justify-between py-3">
                    <div class="text-gray-500 font-extrabold">Suggestions for you</div>
                    <button class="text-blue-500 hover:text-gray-900 text-xs font-extrabold">
                        See All
                    </button>
                </div>

                <div>
                    <Link href="/" class="flex items-center justify-between max-w-[300px] pb-2">
                        <div class="flex items-center">
                            <img class="rounded-full z-10 w-[37px]  h-[37px]" src="https://picsum.photos/id/200/300/320" alt="">
                            <div class="pl-4">
                                <div class="text-black font-extrabold">Name Here</div>
                                <div class="text-gray-500 text-extrabold text-sm">Name Here</div>
                            </div>
                        </div>
                        <button class="text-blue-500 hover:text-gray-900 text-xs font-extrabold">
                            Follow
                        </button>
                    </Link>
                </div>
                <div class="max-w-[300px] mt-5">
                    <div class="text-sm text-gray-400">About Help Press API Jobs Privacy Terms Locations Language Meta Verifies</div>
                    <div class="text-left text-gray-400 mt-4"> 2025 INSTAGRAM FROM META</div>
                </div>
            </div>
        </div>

        <div id="BottomNav" class="fixed z-30 bottom-0 w-full md:hidden flex items-center justify-around bg-white border-t py-2 border-t-gray-300">
            <Link href="/">
                <HomeOutline fillColor="#000000" :size="33" class="cursor-pointer" />
            </Link>
            <Compass fillColor="#000000" :size="33" class="cursor-pointer" />
            <SendOutline fillColor="#000000" :size="33" class="cursor-pointer" />
            <Plus @click="$event => showCreatePost - true" fillColor="#000000" :size="33" class="cursor-pointer" />
            <AccountPlusOutline fillColor="#000000" :size="33" class="cursor-pointer" />
            <Link href="/">
                <img class="rounded-full w-[30px] cursor-pointer" src="https://picsum.photos/id/200/300/320" alt="">
            </Link>
        </div>
    </div>

    <CreatePostOverlay v-if="showCreatePost" @close="$event => showCreatePost = false" />

</template>

<style scoped>

</style>
