<script setup>
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

</script>

<template>
  

    <h2 class="pt-24 text-4xl font-bold text-center text-gray-800 dark:text-white mb-12"  >💼 My Skills</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-10 max-w-6xl mx-auto">
      <div
        v-for="skill in skills"
        :key="skill.name"
        class="group relative bg-white dark:bg-gray-800 rounded-xl shadow-md hover:shadow-2xl transition-shadow duration-300 p-6 overflow-hidden"
      >
        <div class="absolute inset-0 bg-gradient-to-r from-blue-500 to-indigo-500 opacity-0 group-hover:opacity-10 transition-opacity duration-300 rounded-xl"></div>

        <div class="flex justify-between items-center mb-4">
          <h3 class="text-xl font-semibold text-gray-700 dark:text-gray-200 group-hover:text-blue-600 transition-colors duration-300">
            {{ skill.name }}
          </h3>
          <span class="text-sm text-gray-500 dark:text-gray-400">{{ skill.level }}%</span>
        </div>

        <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-3">
          <div
            class="bg-gradient-to-r from-blue-500 to-indigo-500 h-3 rounded-full transition-all duration-500"
            :style="{ width: skill.level + '%' }"
          ></div>
        </div>

        <p class="mt-4 text-sm text-gray-600 dark:text-gray-400 group-hover:text-gray-800 dark:group-hover:text-gray-200 transition-colors duration-300">
          {{ skill.description }}
        </p>
      </div>
    </div>
 
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      skills: [
        {
          name: 'Html',
          level: 90,
         
        },
        {
          name: 'CSS',
          level: 80,
          
        },
        {
          name: 'Java',
          level: 80,
          
        },
        {
          name: 'Pyhon',
          level: 80,
          
        },
        {
          name: 'Copilot',
          level: 99,
          
        },
        {
          name: 'ChatGPT',
          level: 99,
          
        },
      ],
    };
  },
};
</script>

