<template>
  <div class="z-10 transition-all fixed"
  :class="managerStore.sidebar ? ['translate-x-[0]']: ['translate-x-[-100%]']">
    <div
      class="bg-white dark:bg-dark-grey min-h-[calc(100vh-60px)] w-64 lg:w-[300px] pb-10 hidden sm:flex sm:flex-col border-r border-r-lines-light dark:border-r-lines-dark">
      <p class="text-medium-grey text-xs py-4 px-6 font-bold">ALL BOARDS ({{ boardsStore.boards.length }})</p>
      <div @click="onClickBoard(index)" v-for="(board, index) in boardsStore.boards" :key="index"
        class="flex items-center gap-2 px-6 py-2 cursor-pointer text-medium-grey   "
        :class="board?.name === boardsStore?.getCurrentBoard?.name ?
        ['bg-main-blue', 'text-white', 'fill-white', 'hover:bg-main-blue-light']
        :
        ['fill-medium-grey', 'hover:text-main-blue', 'hover:fill-main-blue', 'hover:bg-main-blue/10']">
        <IconBoard />
        <span>{{ board.name }}</span>
      </div>
      <div @click="createNewBoard()"
        class=" flex items-center gap-2 px-6 py-2 cursor-pointer fill-main-blue text-main-blue hover:bg-medium-grey/10">
        <IconBoard />
        <span>+ Create New Board</span>
      </div>
      <div class="flex flex-col gap-2 mt-auto">
        <DarkModeSwitch class="w-10/12 mx-auto " />
        <HideSidebar/>
      </div>
    </div>
  </div>
</template>
<script setup>
import { useManagerStore } from '@/stores/manager';
import { useBoardsStore } from '@/stores/boards';
import IconBoard from '@/components/icons/IconBoard.vue';
import DarkModeSwitch from './sidebar/DarkModeSwitch.vue';
import HideSidebar from './sidebar/HideSidebar.vue';
const managerStore = useManagerStore()
const boardsStore = useBoardsStore()

const onClickBoard = (index) => {
  boardsStore.selectedBoard = index
}
const createNewBoard = () => {
  managerStore.overlay = true
  managerStore.boardForm = { visible: true, edit: false }
}
</script>