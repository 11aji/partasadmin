<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import Carousel from '@/Components/Carousel.vue';
import { Head } from '@inertiajs/vue3';

</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <div class="flex justify-center">
            <div class="p-6 dark:border-gray-700 mt-14 bg-blue-400">
                <img src="/partas_logo.png" class="h-40 mx-auto mb-4" alt="FlowBite Logo" />
                <h1 class="text-4xl font-bold text-center mb-8">WELCOME TO PARTAS BUS INC</h1>

                <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
                    <div>
                        <img class="h-auto max-w-full rounded-lg" src="/partas-bus-1.jpg" alt="">
                    </div>
                    <div>
                        <img class="h-auto max-w-full rounded-lg" src="/partas-bus-2.jpg" alt="">
                    </div>
                    <div>
                        <img class="h-auto max-w-full rounded-lg" src="/partas-bus-3.jpg" alt="">
                    </div>
                    <div>
                        <img class="h-auto max-w-full rounded-lg" src="/partas-bus-4.jpeg" alt="">
                    </div>
                    <div>
                        <img class="h-auto max-w-full rounded-lg" src="storage/images/carousel1.png" alt="">
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

