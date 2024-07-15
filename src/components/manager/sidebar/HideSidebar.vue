<template>
  <div @click="onClickHide"
    class="cursor-pointer flex items-center gap-2 px-6 py-2 font-bold text-medium-grey group hover:bg-main-blue/10 dark:hover:bg-white hover:text-main-blue">
    <IconHideSidebar class="fill-medium-grey group-hover:fill-main-blue" />
    <p class="">Hide Sidebar</p>
  </div>
</template>
<script setup>
import { useManagerStore } from '@/stores/manager';
import IconHideSidebar from '../../icons/IconHideSidebar.vue';

const managerStore = useManagerStore()
const onClickHide = () => {
  managerStore.sidebar = false
}
</script>