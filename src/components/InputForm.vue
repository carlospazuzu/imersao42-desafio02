<template>
    <div class="grid-x grid-margin-x" id="inputForm">
        <div class="cell small-3">
            <input type="number" v-model="timeSpent" placeholder="Time spent" min="1">
        </div>
        <div class="cell small-3">
            <select v-model="workoutType" >
                <option>Run</option>
                <option>Swimming</option>
                <option>Bike</option>
            </select>
        </div>
        <div class="cell small-3">
            <input v-model="workoutDate" type="date" />
        </div>
        <div class="cell small-3">
            <button @click="add(timeSpent, workoutType, workoutDate)" type="button" class="button expanded">Add</button>
        </div>        
    </div>
</template>



<script>
export default {
    props: {
        add: Function
    },
    data: function() {
        return {
            timeSpent: 1,
            workoutType: 'Run',
            workoutDate: ''
        }
    }
}
</script>

<style scoped>

#inputForm {
    border: 1px solid #666;
    padding: 20px 40px;
    border-radius: 4px;
    margin: 0px 20px;
}

#right {
    float: right;
}
</style>