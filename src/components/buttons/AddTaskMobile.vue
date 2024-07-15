<template>
  <div class="sm:hidden min-w-[48px]">
    <button @click="addTask" type="button" v-bind="$attrs" :disabled="!boardsStore.getColumns"
      class="text-white text-sm font-bold p-2.5 rounded-full bg-main-blue hover:bg-main-blue-light disabled:bg-main-blue disabled:bg-opacity-20">
      <img src="@/assets/icons/icon-add-task-mobile.svg" alt="">
    </button>
  </div>
</template>
<script setup>
import { useBoardsStore } from '@/stores/boards';
import { useManagerStore } from '@/stores/manager';
const boardsStore = useBoardsStore()
const managerStore = useManagerStore()

const addTask = () => {
  managerStore.overlay = true
  managerStore.taskForm = { edit: false, visible: true }
}
</script>