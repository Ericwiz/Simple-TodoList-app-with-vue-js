<template>
  <v-container class="w-75 mx-auto">
    <div class="d-flex flex-column align-center flex-md-shrink-1">
      <h1 class="text-center">#todo</h1>
      <div class="w-100">
        <div class="d-flex flex-row justify-space-between mb-6 w-100 botom">
          <v-btn flat text 
          v-for="tab in tabs"
          :key="tab"
          @click="currentTab = tab"
          class="text-body-1 mt-6 effect"
          color=""
          >{{ tab }}</v-btn>
          <hr>
        </div>

        <component :is="currentTab"><TheTodos /></component>
      </div>
    </div>
  </v-container>
</template>

<script>
import Active from './ActiveTodos.vue';
import All from './AllTodos.vue';
import Completed from './CompletedTodos.vue';
import TheTodos from './TheTodos.vue';

  export default {
    components: { All, Active, Completed, TheTodos },
    data() {
      return {
        currentTab: 'All',
        tabs: [
          'All',
          'Active',
          'Completed'
        ],

        
      }
    }
}
</script>

<style scoped>
.botom {
  border-bottom: 1px solid grey;
}
.effect {
  border-bottom: 0 solid blue;
}

.effect:focus {
  border-bottom: 3px solid blue;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
  transition: all;
  transition-duration: 0.5ms;
}
</style>