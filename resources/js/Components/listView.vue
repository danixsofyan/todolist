<script setup>
import listItem from '@/Components/listItem.vue';
import listView from '@/Components/listView.vue';
</script>
<template>
    <div class="mt-4">
        <h4>list item</h4>
        <hr class="m-auto mb-3 w-50" />
        <ul class="m-auto list-group">
            <list-item
                :item="item"
                v-on:itemchanged="$emit('reloadlist')"
                v-for="item in items"
                :key="item.id"
                class="m-auto my-1 text-justify text-wrap"
            />
        </ul>
    </div>
</template>

<script>

export default {
    components: {
        listItem
    },
    props: ["items"]
};
</script>

<style scoped></style>
