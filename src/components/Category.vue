<template>
    <div class="border border-blue-500 p-2">
        {{ category.name }}: ({{ category.child.length }})
        <button class="btn" @click="add">Add</button>
        <Category 
            v-for="child in category.child"
            :key="child.name"
            :category="child"
            @add="addChildCategory"
        />
    </div>
</template>

<script setup>
const { category } = defineProps(['category'])
const emit = defineEmits(['add'])

const add = () => {
    const newChild = {
        name: `child${category.child.length + 1}`,
        child: [],
    }
    emit('add', category, newChild)
}

const addChildCategory = (category, childCategory) => {
    emit('add', category, childCategory)
}
</script>
