<script setup>
    import { RouterLink } from 'vue-router';
    import useSkills from '../../composables/skills';
    import { onMounted } from 'vue';

    const {skill, skills, getSkills, destroySkill} = useSkills();

    onMounted(() => getSkills());
</script>

<template>
    <div class="mt-12">
        <div class="flex justify-end m-2 p-2">
                <RouterLink :to="{name: 'SkillCreate'}" class="bg-slate-500 px-8 py-2 rounded text-white hover:bg-slate-700">Add New Skill</RouterLink>
        </div>
        <div class="relative overflow-x-auto">
            <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            Name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Slug
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Category
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="skill in skills" :key="skill.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            {{ skill.name }}
                        </th>
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            {{ skill.slug }}
                        </th>
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            <RouterLink :to="{name: 'SkillEdit', params: {id: skill.id}}" class="mx-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                                Edit
                            </RouterLink>
                            <button @click="destroySkill(skill.id)" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2 text-center dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-800">
                                Delete
                            </button>
                        </th>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>