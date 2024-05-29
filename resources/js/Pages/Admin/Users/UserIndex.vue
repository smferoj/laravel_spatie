<script setup>
import AdminLayout from '@/Layouts/AdminLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
import Table from '../../../Components/Parts/Table.vue';
import TableRow from '../../../Components/Parts/TableRow.vue';
import TableHeaderCell from '../../../Components/Parts/TableHeaderCell.vue';
import TableDataCell from '../../../Components/Parts/TableDataCell.vue';

const props = defineProps(['users']);
console.log(props.users);
</script>

<template>
    <Head title="Users index" />
    <AdminLayout>
        <div class="max-w-7xl mx-auto py-4">
                <div class="flex justify-between">
                     <h1> Users Inde Page</h1>
                     <Link :href="route('users.create')" class="text-white px-2 py-2 mb-2 font-semibold bg-indigo-500 hover:bg-indigo-700 rounded" > Add User </Link>
                </div>
                    <Table>
                        <template #header>
                         <TableRow>
                            <TableHeaderCell>ID</TableHeaderCell>
                            <TableHeaderCell>Name</TableHeaderCell>
                            <TableHeaderCell>Email</TableHeaderCell>
                            <TableHeaderCell>Action</TableHeaderCell>
                         </TableRow>
                        </template>
                        <template #default >
                          <TableRow v-for="user in users" :key="user.id" class="border-b">
                          <TableDataCell> {{ user.id }}</TableDataCell>
                          <TableDataCell> {{ user.name }}</TableDataCell>
                          <TableDataCell> {{ user.email }}</TableDataCell>
                          <TableDataCell  class="space-x-4"> 
                            <Link :href="route('users.edit', user.id)" class="text-green-400 hover:text-green-600">Edit</Link>
                            <Link :href="route('users.destroy', user.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">Delete</Link>
                          </TableDataCell>
                          </TableRow>
                        </template >
                    </Table>
                </div>
    </AdminLayout>
</template>
