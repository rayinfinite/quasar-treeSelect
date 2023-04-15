<template>
  <div class="q-pa-md">
    <q-select ref="treeSelect" filled v-model="model" :options="options" label="Filled">
      <template v-slot:option="scope">
        <q-tree :nodes="[scope.opt]" default-expand-all v-model:selected="model" node-key="label" />
      </template>
    </q-select>
  </div>
</template>
<script setup>
import { ref, watch } from "vue";
const model = ref(null);
const treeSelect = ref(null);
const options = [
  {
    label: "Satisfied customers (with avatar)",
    avatar: "https://cdn.quasar.dev/img/boy-avatar.png",
    children: [
      {
        label: "Good food (with icon)",
        icon: "restaurant_menu",
        children: [{ label: "Quality ingredients" }, { label: "Good recipe" }],
      },
      {
        label: "Good service (disabled node with icon)",
        icon: "room_service",
        disabled: true,
        children: [{ label: "Prompt attention" }, { label: "Professional waiter" }],
      },
      {
        label: "Pleasant surroundings (with icon)",
        icon: "photo",
        children: [
          {
            label: "Happy atmosphere (with image)",
            img: "https://cdn.quasar.dev/img/logo_calendar_128px.png",
          },
          { label: "Good table presentation" },
          { label: "Pleasing decor" },
        ],
      },
    ],
  },
];

watch(model, () => {
  treeSelect.value.hidePopup();
});
</script>
