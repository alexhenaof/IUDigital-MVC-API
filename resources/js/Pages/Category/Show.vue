<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link  } from '@inertiajs/vue3';

defineProps({
    category: {
        type: Object,
    },
});

</script>

<template>
    <Head title="Categories" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Categories</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white dark:bg-gray-800 overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900 dark:text-gray-100">

                        <h2 class="text-center">Detalles de categoria</h2>
 
                        <div><label for="name">id: {{ category.id }}</label></div>
                        <div><label for="name">Nombre: {{ category.name }}</label></div>
                        <div><Link :href="'/categories/'+ category.id + '/edit'" >Editar</Link></div>

                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
