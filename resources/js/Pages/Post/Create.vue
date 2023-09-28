<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm  } from '@inertiajs/vue3';
import { router } from '@inertiajs/vue3';

defineProps({
    errors: {
        type: Array,
    },
    categories: {
        type: Array
    }
});

const form = useForm({
    title: null,
    message: null,
    category_id: null
})

function submit() {
  router.post('/posts', form)
}
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

                        <h2 class="text-center">Crear post</h2>
 
                        <form @submit.prevent="submit">
                            <label for="title">Titulo:</label>
                            <input id="title" v-model="form.title" />
                            <div v-if="errors.title">{{ errors.title }}</div>

                            <label for="message">Mensaje:</label>
                            <input id="message" v-model="form.message" />
                            <div v-if="errors.message">{{ errors.message }}</div>

                            <label for="category_id">Categoria:</label>
                            <select v-model="form.category_id">
                                <option disabled value="">Seleccione un elemento</option>
                                <option v-for="category in categories" :key="category.id" :value="category.id">{{category.name}}</option>
                            </select>
                            <div v-if="errors.category_id">{{ errors.category_id }}</div>

                            <div><button type="submit">Crear</button></div>
                        </form>

                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
