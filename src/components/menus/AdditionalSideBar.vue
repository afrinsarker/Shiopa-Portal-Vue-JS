<template>
  <div class="h-screen bg-white overflow-hidden z-20 relative shadow-lg">
    <div class="m-4">
      <div class="text-lg text-gray-500 pb-6">{{ singleMenu.name }}</div>
      <div v-for="(item, index) in singleMenu.submenus" :key="index" class="pb-3">
        <router-link :to="singleMenu.url + item.url" class="cursor-pointer text-blue-800" @click="$emit('closeAdditionalSidebar')">
          <div class="flex flex-nowrap  text-gray-700 p-1">
            <img :src="singleMenu.icon" class="dashboard-submenu-icon mr-4" />
            {{ item.name }}
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { MenuItem } from '@/types/SideBar'

export default defineComponent({
  name: 'AdditionalSideBar',
  props: {
    singleMenu: {
      type: Object as PropType<MenuItem>,
      required: true
    },
  },
  methods: {
    handleDebug():void {
      console.log(this.singleMenu)
    }
  }
});
</script>