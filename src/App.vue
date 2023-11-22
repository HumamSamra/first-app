<template>
  <v-app>
    <v-navigation-drawer :width="251" v-model="drawer">
      <v-list-item title="My Application" subtitle="Vuetify" value="title" class="my-3"></v-list-item>
      <v-divider></v-divider>
      <v-list nav>
        <v-list-item prepend-icon="mdi-home-outline" subtitle="Navigate to homepage" title="Home"
          value="home"></v-list-item>
        <v-list-item prepend-icon="mdi-format-list-bulleted" subtitle="Navigate to finished tasks" title="Current Tasks"
          value="list"></v-list-item>
        <v-list-item prepend-icon="mdi-format-list-text" subtitle="Navigate to finished tasks" title="Finished"
          value="finished"></v-list-item>
        <v-list-item prepend-icon="mdi-calendar-check" subtitle="Navigate to finished tasks" title="Finished"
          value="incomplete"></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-toolbar elevation="2" color="accent">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>ToDo List</v-toolbar-title>

      <v-spacer></v-spacer>



      <v-menu>
        <template v-slot:activator="{ props }">
          <v-btn icon="mdi-dots-vertical" v-bind="props"></v-btn>
        </template>
        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index" :value="index">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <template v-slot:extension>
        <v-container centered>
          <v-tabs fixed-tabs>
            <v-tab>
              Todo List
            </v-tab>
            <v-tab>
              Finished
            </v-tab>
            <v-tab>
              Incomplete
            </v-tab>
          </v-tabs>
        </v-container>
      </template>
    </v-toolbar>

    <v-main>
      <HomePage />
    </v-main>
  </v-app>
</template>

<script>
import HomePage from './components/HomePage.vue';

export default {
  name: 'App',
  components: {
    HomePage
  },
  data: () => ({
    drawer: null,
    items: [
      { title: 'Create' },
      { title: 'Settings' },
      { title: 'Theme' },
    ],
  }),
}
</script>
