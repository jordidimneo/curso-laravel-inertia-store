<template>
    <AppLayout title="Create Category">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">
                Edit Category
            </h2>
        </template>

        <div>
            <div class="max-w-7xl mx-auto py-10 sm:px-6 lg:px-8">
                <FormSection @submitted="submit">
                    <template #title>
                        Edit Category
                    </template>
                    <template #description>
                        Edit Category
                    </template>
                    <template #form>
                        <div class="col-span-6 sm:col-span-4">
                            <InputLabel for="">Title</InputLabel>
                            <InputError :message="errors.title">{{ errors.title }}</InputError>
                            <TextInput class="block w-full mt-1" type="text" v-model="form.title" />
                            <InputError :message="errors.slug">{{ errors.slug }}</InputError>
                            <InputLabel for="">Slug</InputLabel>
                            <TextInput class="block w-full mt-1" type="text" v-model="form.slug" />
                        </div>
                    </template>
                    <template #actions>
                        <PrimaryButton :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Edit
                        </PrimaryButton>
                    </template>
                </FormSection>

            </div>
        </div>
    </AppLayout>
</template>



<script>
import { useForm, router } from "@inertiajs/vue3";

import AppLayout from '@/Layouts/AppLayout.vue';
import FormSection from '@/Components/FormSection.vue';
import InputLabel from '@/Components/InputLabel.vue';
import InputError from '@/Components/InputError.vue';
import TextInput from '@/Components/TextInput.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';

export default {

    components: {
        AppLayout,
        FormSection,
        InputLabel,
        InputError,
        TextInput,
        PrimaryButton,
    },
    props: {
        errors: Object,
        category: Object
    },


    setup(props) {

        const form = useForm({
            id: props.category.id,
            title: props.category.title,
            slug: props.category.slug,
        })

        function submit() {
            router.put(route("category.update", form.id), form)
        }

        return { form, submit }

    }
}
</script>