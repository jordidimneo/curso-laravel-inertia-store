<template>
    <AppLayout>
        <div class="container">
            <div class="card">
                <Link class="link-button-default my-4" :href="route('category.create')">Crear</Link>

                <table class="w-full">
                    <thead class="bg-gray-100">
                        <tr class="border-b">
                            <th class="p-3">Id</th>
                            <th class="p-3">Title</th>
                            <th class="p-3">Slug</th>
                            <th class="p-3">Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr class="border-b" v-for="c in categories.data" key="c.id">
                            <td class="p-2">{{ c.id }}</td>
                            <td class="p-2">{{ c.title }}</td>
                            <td class="p-2">{{ c.slug }}</td>
                            <td class="p-2">
                                <Link class="text-sm text-gray-800 mx-2" :href="route('category.edit', c.id)">Edit</Link>
                                <Link as="button" type="button" method="DELETE" class="text-sm text-red-600 mx-2" :href="route('category.destroy', c.id)">Delete</Link>
                            </td>
                        </tr>
                    </tbody>
                </table>
                <!--<template v-for="l in categories.links">
        <Link v-if="!l.active" class="px-2 py-1" :key="l" :href="l.url" v-html="l.label" />
        <span v-else class="px-2 py-1 cursor-pointer text-gray-500" v-html="l.label" />
</template>-->

                <Pagination class=" my-4" :links="categories" />
            </div>

        </div>




    </AppLayout>
</template>

<script>

import Pagination from '@/Shared/Pagination.vue'
import { Link } from "@inertiajs/vue3"

import AppLayout from "@/Layouts/AppLayout.vue"

export default {

    components: {
        AppLayout,
        Link,
        Pagination
    },
    props: {
        categories: Object
    }



}
</script>