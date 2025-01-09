<script setup>
import { ref, onMounted, toRefs, reactive } from "vue";
import { Head, Link, router } from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

import Cog from "vue-material-design-icons/Cog.vue";
import Grid from "vue-material-design-icons/Grid.vue";
import PlayBoxOutline from "vue-material-design-icons/PlayBoxOutline.vue";
import BookmarkOutline from "vue-material-design-icons/BookmarkOutline.vue";
import AccountPlusOutline from "vue-material-design-icons/AccountPlusOutline.vue";

// aklfjaskfjklasjfkjakflaskfjaklsfjkl

let data = reactive({ post: null });
const form = reactive({ file: null });
</script>

<template>
    <Head title="Instagram" />

    <MainLayout class="flex items-start">
        <div class="w-1/4">
            <div class="flex items-center justify-center">
                <img
                    src="https://picsum.photos/200/200"      

                    class="w-20 h-20 rounded-full"  kancillas            
    </MainLayout>
</template>
