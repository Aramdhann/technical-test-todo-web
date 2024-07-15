<template>
  <label class="cursor-pointer bg-light-grey dark:bg-very-dark-grey dark:hover:bg-main-blue/10 py-2 px-4 flex items-center gap-4 rounded-lg
  hover:bg-main-blue hover:bg-opacity-25" :for="subtask?.title">
    <div class="relative">
      <input class="cursor-pointer " v-model="subtask.isCompleted" type="checkbox" :id="subtask?.title">
      <div class="h-4 w-4 rounded-sm flex items-center justify-center absolute 
      top-1/2 left-1/2 translate-y-[-50%] translate-x-[-50%]"
        :class="subtask.isCompleted ? checkbox.checked : checkbox.unchecked">
        <img v-if="subtask.isCompleted" src="@/assets/icons/icon-check.svg" alt="">
      </div>
    </div>
    <span class="text-black dark:text-white text-xs"
      :class="subtask.isCompleted ? 'line-through text-opacity-50 dark:text-opacity-30' : ''">
      {{ subtask?.title }}
    </span>
  </label>
</template>
<script setup>

const props = defineProps({
  subtask: null
})

const checkbox = {
  checked: ['bg-main-blue'],
  unchecked: ['bg-white', 'border', 'border-medium-grey', 'border-opacity-25, dark:bg-dark-grey dark:border-opacity-25']
}

</script>