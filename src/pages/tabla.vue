<template>
    <Navbar />
    <v-container>
        <v-data-table :headers="headers" :items="todos" class="elevation-1"></v-data-table>
    </v-container>
</template>
  
<script>
import { TabPanel } from '@headlessui/vue';
import axios from 'axios';
import Navbar from '../components/Navbar'

export default {
    data: () => ({
        todos: [], // Aquí se almacenarán los datos de la API
        headers: [ // Define los encabezados de la tabla
            { title: 'ID', key: 'id' },
            { title: 'Title', key: 'title' },
            { title: 'Completed', key: 'completed' },
        ],
    }),
    created() {
        this.fetchData();
    },
    methods: {
        async fetchData() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/todos');
                this.todos = response.data;
            } catch (error) {
                console.error('There was an error fetching the data:', error);
            }
        }

    },
};

</script>
  