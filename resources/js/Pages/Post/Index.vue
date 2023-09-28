<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    posts: {
        type: Array,
    },
});
</script>

<template>
    <Head title="Posts" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Posts</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white dark:bg-gray-800 overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900 dark:text-gray-100">
                        <h2 class="text-center">Lista de posts</h2>
 
                        <Link href="/posts/create">Nuevo</Link>

                        <table class="table">
                            <thead>
                            <tr>
                                <th>ID</th>
                                <th>Titulo</th>
                                <th>Mensaje</th>
                                <th>Categoria</th>
                                <th>Actions</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="post in posts" :key="post.id">
                                <td><Link :href="'posts/'+ post.id">{{ post.id }}</Link></td>
                                <td>{{ post.title }}</td>
                                <td>{{ post.message }}</td>
                                <td>{{ post.category.name }}</td>
                                <td>
                                    <div class="btn-group" role="group">
                                        <Link :href="'/posts/'+ post.id + '/edit'" >Editar</Link>
                                        <Link :href="'/posts/'+ post.id" method="delete">Borrar</Link>
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
