<template>
    <div class="grid-container">   
            <table class="hover">
                <thead>
                    <tr>
                    <th>Tempo</th>
                    <th>Tipo</th>
                    <th>Data</th>
                    <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="log in logs" :key="log.id">
                        <td>{{ String(log.time) + 'h' }}</td>
                        <td>{{ log.type }}</td>
                        <td>{{ log.date }}</td>
                        <td>
                            <button @click="deleteLog(log.id)" type="button" class="alert button">Delete</button>
                        </td>
                    </tr>
                </tbody>
            </table>            
            <h2 v-if="totalHours > 0">{{ totalHours }} hours of exercises</h2> 
    </div>    
</template>

<script>
export default {
    props: {
        logs: Array,
        deleteLog: Function,
        totalHours: Number
    }
}
</script>

<style scoped>
    h2 {
        text-align: center;
        margin-top: 20px;
    }
</style>