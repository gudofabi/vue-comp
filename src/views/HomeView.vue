
<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>

    <div class="">
      <button @click="decreaseCounter" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter" class="btn">+</button>
    </div>

    <p>This counter is {{ oddOrEven }} </p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" v-autofocus>
    </div>
  
  </div>
</template>

<script setup>
/**
 * imports
 */
  import { computed, onMounted, reactive, watch } from 'vue';
  import { vAutofocus } from '@/directives/vAutofocus';

/**
 *  App Title
 */
  const appTitle = 'My Amazing Counter'

  onMounted(() => {
    console.log('Do stuff related to App Title')
  })


/**
 * Counter
 */
  const counterData = reactive({
    count: 0,
    title: 'My title'
  })

  watch(() => counterData.count, (newCount) => {
    if(newCount == 20) console.log('You hit 20!');
  });

  const oddOrEven = computed(() => { 
    if(counterData.count % 2 === 0) return 'even'
    return 'odd'
  })

  const increaseCounter = () => {
    counterData.count++
  }

  const decreaseCounter = () => {
    counterData.count--
  }

  onMounted(() => {
    console.log('Do stuff related to Counter')
  })


</script>

<style scoped>
.home {
  text-align: center;
  padding: 20px;

}

.btn, .counter {
  font-size: 40px;
  margin: 10px;

}

.edit {
  margin-top: 60px;

}
</style>

