<script setup>
    import useSkills from '../../composables/skills';
    import { onMounted } from 'vue';

    const { skill, getSkill, updateSkill, errors } = useSkills();

    const props = defineProps({
        id: {
            required: true,
            type: String
        },
    });
    onMounted(() => getSkill (props.id));
</script>

<template>
    <div class="mt-12">
        <form class="max-w-md mx-auto p-4 bg-white shadow-md rounded-md" @submit.prevent="updateSkill($route.params.id)">
            <div class="mb-6">
                <label for="name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-black">Name</label>
                <input type="text" id="name" v-model="skill.name" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="skill name here">
                <div v-if="errors.name">
                    <span class="text-red-500">{{ errors.name[0] }}</span>
                </div>
            </div> 
            <div class="mb-6">
                <label for="slug" class="block mb-2 text-sm font-medium text-gray-900 dark:text-black">Slug</label>
                <input type="text" id="slug" v-model="skill.slug" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="skill slug here">
                <div v-if="errors.slug">
                    <span class="text-red-500">{{ errors.slug[0] }}</span>
                </div>
            </div>
            <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
        </form>
    </div>
</template>