<template>
    <main>
        <div>
            <DataTable :value="data.listeClients" paginator :rows="5" tableStyle="min-width: 50rem">
                <Column field="code" header="Code" style="width: 25%"></Column>
                <Column field="societe" header="Société" style="width: 25%"></Column>
                <Column field="contact" header="Contact" style="width: 25%"></Column>
                <Column field="adresse.ville" header="Ville" style="width: 25%"></Column>
            </DataTable>
        </div>
    </main>
</template>

<script setup>
import { reactive, onMounted } from "vue";
import { doAjaxRequest } from "@/api";
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';

let data = reactive({
    listeClients: []
});

function showError(error) {
    console.log("Erreur : status %d", error.status)
    console.log(error.body);
    alert(error.message);
}

function chargeClients() {
    doAjaxRequest("/api/clients")
        .then((json) => {
            data.listeClients = json._embedded.clients;
        })
        .catch(showError);
}

// A l'affichage du composant, on affiche la liste
onMounted(chargeClients);

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
