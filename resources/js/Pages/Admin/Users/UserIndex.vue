<script setup>
import AdminLayout from '@/Layouts/AdminLayout.vue';
import { Head } from '@inertiajs/vue3';
import Table from '../../../Components/Parts/Table.vue';
import TableRow from '../../../Components/Parts/TableRow.vue';
import TableHeaderCell from '../../../Components/Parts/TableHeaderCell.vue';
import TableDataCell from '../../../Components/Parts/TableDataCell.vue';

const props = defineProps(['users']);
console.log(props.users);
</script>

<template>
    <Head title="Dashboard" />
    <AdminLayout>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">Users Index Page </div>
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
                          <TableDataCell>  Edit/Delete </TableDataCell>
                          </TableRow>
                        </template >
                    </Table>
                </div>
            </div>
        </div>
    </AdminLayout>
</template>
