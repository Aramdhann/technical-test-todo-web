<template>
  <header class="bg-white dark:bg-dark-grey top-0 left-0 w-full flex items-center sm:pr-4">
    <div class="hidden items-center sm:flex pl-6 border-r border-r-lines-light dark:border-r-lines-dark"
      :class="managerStore.sidebar ? ['min-w-[256px]', 'lg:min-w-[300px]'] : ['min-w-[200px]']">
      <h1 class="text-2xl dark:text-white text-black font-bold">Todo List</h1>
    </div>
    <div class="mx-auto max-w-sm w-11/12 flex items-center h-16 gap-4">
      <div @click="showMobileBar" class="flex items-center gap-2 group cursor-pointer sm:hidden">
        <h1 class="text-black dark:text-white font-bold text-lg cursor-pointer">{{ boardsStore.getCurrentBoard?.name }}
        </h1>
        <IconArrowDown v-if="!managerStore.sidebarMobile" />
        <IconArrowUp v-else />
      </div>
      <h1 class="text-black dark:text-white font-bold hidden text-lg ms-6 sm:block">
        {{ boardsStore.getCurrentBoard?.name }}
      </h1>
      <div v-if="boardsStore.boards.length" class="flex items-center gap-4 ml-auto">
        <AddButtonMobile />
        <PrimarySmall @click="addTask" class="hidden sm:block">+ Add Todo Task</PrimarySmall>
        <Dropdown target="Board" @onClickEdit="editTask" @onClickDelete="deleteTask" />
      </div>
    </div>
  </header>
</template>
<script setup>
import AddButtonMobile from '@/components/buttons/AddTaskMobile.vue'
import { useBoardsStore } from '@/stores/boards';
import { useManagerStore } from '@/stores/manager';
import Dropdown from '@/components/manager/Dropdown.vue';
import IconArrowDown from './icons/IconArrowDown.vue';
import IconArrowUp from './icons/IconArrowUp.vue';
import PrimarySmall from './buttons/PrimarySmall.vue';

const boardsStore = useBoardsStore()
const managerStore = useManagerStore()

const editTask = () => {
  managerStore.overlay = true
  managerStore.boardForm = { edit: true, visible: true }
}
const deleteTask = () => {
  managerStore.overlay = true
  managerStore.delete = { board: true, visible: true }
}
const addTask = () => {
  managerStore.overlay = true
  managerStore.taskForm = { visible: true, edit: false };
}
const showMobileBar = () => {
  managerStore.sidebarMobile = true;
  managerStore.overlay = true
}

</script>