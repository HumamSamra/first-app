<template>
    <v-container>
        <v-text-field v-model="searchInp" clearable label="Search" variant="solo-filled"></v-text-field>
        <h3>Tasks :</h3>
        <v-btn stacked>
            Button
        </v-btn>
    </v-container>
    <v-card>
        <v-list class="container">
            <v-list-item class="p-3 rounded-2 mb-3" v-for="item in items" :value="item.value" :key="item.value">
                <v-list-item-content>
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    <v-list-item-subtitle>{{ item.subtitle }}</v-list-item-subtitle>
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-card>
</template>
<script>
export default {
    name: "HomePage",
    data: () => ({
        searchInp: "",
        items: Array.from({ length: 10 }, (_, index) => ({
            title: `Title ${index + 1}`,
            subtitle: `Sub title ${index + 1} here`,
            value: index
        })),
    }),
    watch: {
        searchInp(newText) {
            this.search(newText);
        },
    },
    methods: {
        search(value) {
            alert(value);
        },
    },
}
</script>