<script setup>
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

const form = useForm({
    name: ""
})
</script>

<template>
  <Head title="Create Roles" />
  <AdminLayout>
    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
          <div class="p-6 text-gray-900 flex justify-between">
            <h1>Role Create Page</h1>
            <Link
              :href="route('roles.index')"
              class="text-white px-2 py-2 font-semibold bg-indigo-500 hover:bg-indigo-700 rounded"
            >
              See Roles
            </Link>
          </div>
           <div class="mt-6 max-w-md mx-auto">
          <form @submit.prevent="form.post(route('roles.store'))">
            <div>
              <InputLabel for="name" value="Name" />
              <TextInput
                id="name"
                type="text"
                class="mt-1 block w-full"
                v-model="form.name"
                autofocus
                autocomplete="username"
              />

              <InputError class="mt-2" :message="form.errors.name" />
            </div>
            <div class="flex items-center mt-6">
              <PrimaryButton
                class="ms-4"
                :class="{ 'opacity-25': form.processing }"
                :disabled="form.processing"
              >
                Create
              </PrimaryButton>
            </div>
          </form>
        </div>
        </div>
      </div>
    </div>
  </AdminLayout>
</template>
