<script setup>
import { Link } from "@inertiajs/vue3";
import { onMounted, ref, toRef } from "vue";
import { Carousel, Slide, Navigation } from "vue3-carousel";
import "vue3-carousel/dist/carousel.css";

import MainLayout from "@/Layouts/MainLayout.vue";
import LikesSection from "@/Components/LikesSection.vue";

import DotsHorizontal from "vue-material-design-icons/DotsHorizontal.vue";

let wWidth = ref(window.innerWidth);
let currentSlide = ref(0);
let crurrentPost = ref(null);
let openOverlay = ref(false);

const props = defineProps({ posts: Object, allUser: Object });
const { posts, allUser } = toRef(props);

onMounted(() => {
    window.addEventListener("resize", () => {
        wWidth.value = window.innerWidth;
    });
});
</script>

<template>
    <!-- <Head title="Instagram" /> -->
    <MainLayout>
        <div class="mx-auto lg:pl-0 md:pl-[80px] pl-0">
            <Carousel
                v-model="currentSlide"
                class="max-w-[700px] mx-auto"
                :items-to-show="wWidth >= 768 ? 8 : 6"
                :items-to-scroll="4"
                :wrap-around="true"
                :transition="500"
                snapAlign="start"
            >
                <Slide v-for="slide in 10" :key="slide" class="h-60">
                    <Link
                        href="/"
                        class="relative mx-auto text-center mt-4 px-2 cursor-pointer"
                    >
                        <div
                            class="absolute z-[-1] -top-[5px] left-[5px] rounded-full rotate-50 h-[64px] contrast-[1.3] bg-gradient-to-t from-yellow-300 to-purple-500 via-red-500"
                        >
                            <div
                                class="rounded-full ml-[3px] mt-[3px] w-[58px] bg-white"
                            ></div>
                        </div>
                        <img
                            class="rounded-full w-[56px] h-[56px] -mt-[1px]"
                            src="https://upload.wikimedia.org/wikipedia/en/thumb/0/04/Hollow_Knight_first_cover_art.webp/274px-Hollow_Knight_first_cover_art.webp.png"
                            alt=""
                        />
                        <div
                            class="text-ss mt-2 w-[60px] truncate text-ellipsis overflow-hidden"
                        >
                            NAME HERE
                        </div>
                    </Link>
                </Slide>

                <template #addons> <Navigation /> </template>
            </Carousel>

            <div id="Posts" class="px-4 max-w-[600px] mx-auto">
                <div class="flex items-center justify-between py-2">
                    <div class="flex items-center">
                        <Link href="/" class="flex items-center">
                            <img
                                src="https://th.bing.com/th/id/OIP.EQt7CAO7EHH8ITjlgxkUZgHaJJ?rs=1&pid=ImgDetMain"
                                class="rounded-full w-[38px] h-[38px]"
                                alt=""
                            />
                            <div class="ml-4 font-extrabold text-[15px]">
                                Mia Malkoval
                            </div>
                        </Link>
                        <div
                            class="flex items-center text-[15px] text-gray-500"
                        >
                            <span class="-mt-5 ml-2 mr-[5px] text-[35px]"
                                >.</span
                            >
                            <div>DATE HERE</div>
                        </div>
                    </div>

                    <DotsHorizontal class="cursor-pointer" :size="27" />
                </div>

                <div
                    class="bg-black rounded-lg w-full min-h-[400px] flex items-center"
                >
                    <img
                        src="https://picsum.photos/id/54/300/320"
                        class="mx-auto w-full"
                        alt=""
                    />
                </div>

                <LikesSection />

                <div class="text-black font-extrabold py-1">3 likes</div>
                <div>
                    <span class="text-black font-extrabold">NAME HERE</span>
                    this is some text here
                </div>
                <button class="text-gray-500 font-extrabold py-1">
                    View all 4 comment
                </button>
            </div>
        </div>
    </MainLayout>
</template>

<style scoped>
.carousel_prev,
.carousel_next,
.carousel_prev:hover,
.carousel_next:hover {
    color: rgb(255, 255, 255);
    border-radius: 100%;
    margin: 0 20px;
}
</style>
