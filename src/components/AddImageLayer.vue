<template>
  <v-layout row wrap>
    <v-flex sm12>
      <v-tabs grow v-model="active">
        <v-tab v-for="tab of tabs" :key="tab.id">
          {{ tab.name }}
        </v-tab>
      </v-tabs>
      <v-tabs-items v-model="active">
        <v-tab-item :value="0">
          <div :style="`background-color:${dummyValue.properties.color}`">
            {{ dummyValue.properties.color }}
          </div>
        </v-tab-item>
        <v-tab-item :value="1">
          <div>{{ dummyValue.name }}</div>
        </v-tab-item>
        <v-tab-item :value="2"> </v-tab-item>
      </v-tabs-items>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  props: {
    dummyValue: {
      default: null,
    },
  },
  data() {
    return {
      active: 0,
      tabs: [
        { id: 0, name: "Tab 1" },
        { id: 1, name: "Tab 2" },
        { id: 2, name: "Tab 3" },
      ],
    };
  },
  mounted() {
    this.addLayer();
  },
  methods: {
    addLayer() {
      console.log("add layer");
    },
  },
};
</script>
