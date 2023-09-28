<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm  } from '@inertiajs/vue3';
import { router } from '@inertiajs/vue3';

const props = defineProps({
    errors: {
        type: Array,
    },
    category: {
        type: Object
    }
});

const form = useForm({
    name: props.category.name,
})

function submit() {
  router.put('/categories/' + props.category.id, form)
}

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

                        <h2 class="text-center">Editar categoria</h2>
 
                        <form @submit.prevent="submit">
                            <label for="name">Nombre:</label>
                            <input id="name" v-model="form.name" />
                            <div v-if="errors.name">{{ errors.name }}</div>
                            <div><button type="submit">Modificar</button></div>
                        </form>

                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
