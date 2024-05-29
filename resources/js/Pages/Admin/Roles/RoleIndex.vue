<script setup>
import AdminLayout from '@/Layouts/AdminLayout.vue';
import { Head } from '@inertiajs/vue3';
import {Link} from '@inertiajs/vue3';
import Table from '../../../Components/Parts/Table.vue';
import TableRow from '../../../Components/Parts/TableRow.vue';
import TableHeaderCell from '../../../Components/Parts/TableHeaderCell.vue';
import TableDataCell from '../../../Components/Parts/TableDataCell.vue';


const props = defineProps(['roles']);
console.log(props.roles);
</script>

<template>
    <Head title="Dashboard" />

    <AdminLayout>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900 flex justify-between"> 
                        <h1> Roloe Index Page</h1>
                        <Link :href="route('roles.create')" class="text-white px-2 py-2 font-semibold bg-indigo-500 hover:bg-indigo-700 rounded" > Add Roles </Link>
                         </div>
                    <Table>
                        <template #header>
                         <TableRow>
                            <TableHeaderCell>ID</TableHeaderCell>
                            <TableHeaderCell>Name</TableHeaderCell>
                            <TableHeaderCell>Action</TableHeaderCell>
                         </TableRow>
                        </template>
                        <template #default >
                          <TableRow v-for="role in roles" :key="role.id" class="border-b">
                          <TableDataCell> {{ role.id }}</TableDataCell>
                          <TableDataCell> {{ role.name }}</TableDataCell>
                          <TableDataCell class="space-x-4">  
                            <Link :href="route('roles.edit', role.id)" class="text-green-400 hover:text-green-600">Edit</Link>
                            <Link :href="route('roles.destroy', role.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">Delete</Link>
                            
                             </TableDataCell>
                          </TableRow>
                        </template >
                    </Table>
                </div>
            </div>
        </div>
    </AdminLayout>
</template>
