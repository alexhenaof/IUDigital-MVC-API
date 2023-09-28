<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    categories: {
        type: Array,
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
                        <h2 class="text-center">Lista de categorias</h2>
 
                        <Link href="/categories/create">Nueva</Link>

                        <table class="table">
                            <thead>
                            <tr>
                                <th>ID</th>
                                <th>Name</th>
                                <th>Actions</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="category in categories" :key="category.id">
                                <td><Link :href="'categories/'+ category.id">{{ category.id }}</Link></td>
                                <td>{{ category.name }}</td>
                                <td>
                                    <div class="btn-group" role="group">
                                        <Link :href="'/categories/'+ category.id + '/edit'" >Editar</Link>
                                        <Link :href="'/categories/'+ category.id" method="delete">Borrar</Link>
                                    </div>
                                </td>
                            </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
