<script setup>
import { ref } from 'vue';
import Navbar from './Navbar.vue';
import Sidebar from './Sidebar.vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/vue3';
import {usePermission} from "@/Components/composables/Permission"
import { onMounted } from 'vue'
import { initFlowbite } from 'flowbite'

onMounted(() => {
    initFlowbite();
})
const showingNavigationDropdown = ref(false);
const {hasRole} = usePermission()
</script>

<template>
    <div class="w-full h-full">
     
     <!-- Navbar -->
           <Navbar/> 
          
     <!-- Endnavbar -->
    
           <Sidebar/>
     <!-- Sidebar -->

     <!-- EndSidebar -->

      <main class="p-4 md:ml-64 h-auto pt-20">
         <slot/>
       </main>
     
    
    <!-- Footer -->

    
     
   </div>
</template>