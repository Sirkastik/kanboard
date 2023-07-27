<script setup lang="ts">
const title = "KanBoard : Manager";

const description = "Kanban Board for task management";

const url = useRuntimeConfig().app.baseURL;

const image =
  "https://getnave.com/blog/wp-content/uploads/2018/03/kanban-board-in-trello.jpg";

useSeoMeta({
  title: title,
  ogTitle: title,
  description: description,
  ogUrl: url,
  ogDescription: description,
  ogImage: image,
  twitterCard: "summary",
  twitterTitle: title,
  twitterDescription: description,
  twitterImage: image,
});

const lanes = ref([
  {
    id: 1,
    title: "Backlog",
  },
  {
    id: 2,
    title: "In Progress",
  },
  {
    id: 3,
    title: "Needs Review",
  },
  {
    id: 4,
    title: "Ready To Deploy",
  },
  {
    id: 5,
    title: "Completed",
  },
]);

const tasks = ref([
  {
    id: 1,
    laneId: 1,
    title: "Update dependencies",
    description: "Bump up Nuxt version to 3.6",
  },
  {
    id: 2,
    laneId: 1,
    title: "Create Login UI",
    description: "Using the UI in this figma, create the nuxt components",
  },
  {
    id: 3,
    laneId: 1,
    title: "Update Nuxt",
    description: "Bump up Nuxt version to 3.6",
  },
  {
    id: 4,
    laneId: 2,
    title: "Create Signup UI",
    description: "Using the UI in this figma, create the nuxt components",
  },
]);
</script>

<template>
  <article class="flex gap-4">
    <SwimLane
      v-for="lane in lanes"
      :key="lane.id"
      :list="tasks.filter((t) => t.laneId == lane.id)"
      :meta="lane"
    />
  </article>
</template>
