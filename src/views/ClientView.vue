<template>
    <main>
        <div>
            <ClientTable />
        </div>
    </main>
</template>

<script setup>
import ClientTable from "../components/ClientTable.vue";
</script>


<style scoped>
td,
th {
    border: 1px solid #ddd;
    padding: 8px;
}

th {
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: left;
    background-color: #232623;
    color: rgb(255, 255, 255);
}
</style>
