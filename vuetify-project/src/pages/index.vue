<!-- <template>
  <Sample1 />
</template> -->
<template>
  <v-layout class="rounded rounded-md border">
    <v-app-bar title="Vue Samples"></v-app-bar>

    <v-navigation-drawer>
      <v-list nav>
        <!-- <v-list-item
          title="HelloWorld"
          @click="currentComponent = HelloWorld"
        ></v-list-item>
        <v-list-item
          title="Sample1"
          @click="currentComponent = Sample1"
        ></v-list-item> -->
        <v-list-item
          v-for="item in menuItems"
          :key="item.id"
          @click="currentComponent = item.content"
        >
          <!-- @click="selected = item.id" -->
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main class="d-flex align-center justify-center">
      <v-container>
        <component :is="currentComponent" />
      </v-container>
    </v-main>
  </v-layout>
</template>

<script lang="ts" setup>
import { shallowRef, computed } from "vue";
import HelloWorld from "../components/HelloWorld";
import Sample1 from "../components/Sample1.vue";

const menuItems = [
  { content: HelloWorld, id: "HelloWorld", title: "HelloWorld" },
  { content: Sample1, id: "Sample1", title: "Sample1" },
];

const currentComponent = shallowRef(HelloWorld);
// const selected = ref("HelloWorld");
// const currentComponent = computed(() => {
//   console.log(selected.value);
//   switch (selected.value) {
//     case "Sample1":
//       return Sample1;
//     default:
//       return HelloWorld;
//   }
// });
</script>
