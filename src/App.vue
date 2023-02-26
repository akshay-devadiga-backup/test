<template>
  <v-layout px-2 row wrap>
    <v-flex xs6 md6>
      <div class="d-flex justify-between align-center mb-3">
        <v-btn icon @click="addItem">
          <v-icon>add</v-icon>
        </v-btn>
      </div>
      {{ openedPanel }}
      <v-expansion-panel focusable :value="0">
        <v-expansion-panel-content
          v-for="(item, i) in items"
          :key="item.name"
          :style="`background-color:${item.panelColor}`"
        >
          <template v-slot:header>
            <div>{{ item.name }} {{ `Id-${i}` }}</div>
          </template>
          <component
            :is="'Add' + item.type + 'Layer'"
            :dummy-value="item.data"
          />
        </v-expansion-panel-content> </v-expansion-panel
    ></v-flex>
    <v-flex xs8 md8> </v-flex>
  </v-layout>
</template>

<script>
import AddShapeLayer from "./components/AddShapeLayer";
import AddImageLayer from "./components/AddImageLayer";
import AddIconLayer from "./components/AddIconLayer";
export default {
  name: "App",
  components: { AddShapeLayer, AddImageLayer, AddIconLayer },
  data() {
    return {
      panel: 0,
      items: [],
      openedPanel: 0,
    };
  },
  mounted() {
    for (var i = 0; i < 1130; i++) {
      this.items.unshift({
        panelColor: "#a9fff7",
        id: this.items.length + 1,
        name: `Shape - ${this.items.length + 1}`,
        type: "Shape",
        data: { name: "icon", properties: { size: 20, color: "#blue" } },
      });
    }
  },
  methods: {
    addItem() {
      this.items.unshift({
        panelColor: "#7a306c",
        name: `New Shape - ${this.items.length + 1}`,
        type: "Shape",
        data: { name: "icon", properties: { size: 20, color: "red" } },
      });
      //this.openedPanel.unshift(true);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
