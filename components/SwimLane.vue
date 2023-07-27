<script setup lang="ts">
type Meta = {
  id: number;
  title: string;
};
type Task = {
  id: number;
  title: string;
  description: string;
};
const props = defineProps<{
  meta: Meta;
  list: Task[];
}>();
const tasks = ref(props.list);

watch(
  () => props.list,
  (value) => (tasks.value = value)
);
const isDragging = ref(false);
</script>

<template>
  <article class="w-full flex flex-col gap-3 p-4 border rounded">
    <h1 class="font-bold">{{ meta.title }}</h1>
    <draggable
      v-model="tasks"
      item-key="id"
      tag="ul"
      class="flex flex-col gap-2"
      @start="isDragging = true"
      @end="isDragging = false"
    >
      <template #item="{ element: task }">
        <div
          class="flex flex-col border-2 rounded px-2 py-2 cursor-grab"
          :class="{ 'cursor-grabbing': isDragging }"
        >
          <span class="font-semibold">{{ task.title }}</span>
          <span>{{ task.description }}</span>
        </div>
      </template>
    </draggable>
  </article>
</template>
