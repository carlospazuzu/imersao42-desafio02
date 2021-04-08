<template>
  <div class="grid-container">
    <h1>Workout Logs</h1>
    <InputForm :add="addWorkout" />    
    <hr />
    <WorkoutList :logs="logs" :deleteLog="deleteLog" :totalHours="totalHours" />    
  </div>
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import WorkoutList from './components/WorkoutList.vue'
import InputForm from './components/InputForm.vue'

export default {
  name: 'App',
  components: {
    WorkoutList,
    InputForm
  },
  data: function() {
    return {
      logs: [],      
    }
  },
  methods: {
    addWorkout: function(timeSpent, workoutType, workoutDate) {
      this.logs.push(
                      {
                        id: this.logs.length + 1,
                        time: timeSpent,
                        type: workoutType,
                        date: workoutDate
                      }
                    )
    },
    deleteLog: function(logId) {
      var pos = -1;
      
      for (var i = 0; i < this.logs.length; i ++) {
        if (this.logs[i].id === logId) {
          pos = i;
          break;
        }
      }

      if (pos === -1) return;

      this.logs.splice(pos, 1);      
    }
  },
  computed: {
    totalHours: function() {
      if (this.logs.length === 0) return 0;

      const reducer = (acc, cur) => acc + cur
      return this.logs.map(el => Number(el.time)).reduce(reducer)
    }
  }
}
</script>

<style>

h1 {
  text-align: center;
  margin-top: 100px;
}

#insertBox {
    
}

</style>
