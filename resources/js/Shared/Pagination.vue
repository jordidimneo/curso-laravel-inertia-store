<template>
    <div>
        <Component v-for="l in links.links" :key="l" :is="!l.active ? 'Link' : 'span'" class="px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white ml-2 hover:bg-gray-50" :class="!l.active ? '' : 'text-gray-500 cursor-pointer px-2 py-1'" :href="l.url" v-html="l.label" />        
    </div>
</template>

<script>
import { Link } from "@inertiajs/vue3"
export default{
    components:{
        Link
    },
    props:{
        links:Object
    }
}

</script>