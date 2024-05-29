<script setup>
import AdminLayout from '@/Layouts/AdminLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
import Table from '../../../Components/Parts/Table.vue';
import TableRow from '../../../Components/Parts/TableRow.vue';
import TableHeaderCell from '../../../Components/Parts/TableHeaderCell.vue';
import TableDataCell from '../../../Components/Parts/TableDataCell.vue';

const props = defineProps(['permissions']);
console.log(props.permissions);
</script>

<template>
    <Head title="Permissions" />

    <AdminLayout>     
            <div class="max-w-7xl mx-auto py-4">
                <div class="flex justify-between">
                     <h1> Permission Index Page</h1>
                     <Link :href="route('permissions.create')" class="text-white px-2 py-2 font-semibold bg-indigo-500 hover:bg-indigo-700 rounded" > Add Permission </Link>
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
                          <TableRow v-for="permission in permissions" :key="permission.id" class="border-b">
                          <TableDataCell> {{ permission.id }}</TableDataCell>
                          <TableDataCell> {{ permission.name }}</TableDataCell>
                          <TableDataCell class="space-x-4">  
                            <Link :href="route('permissions.edit', permission.id)" class="text-green-400 hover:text-green-600">Edit</Link>
                            <Link :href="route('permissions.destroy', permission.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">Delete</Link>
                            
                             </TableDataCell>
                          </TableRow>
                        </template >
                    </Table>
                
            </div>
   
    </AdminLayout>
</template>
