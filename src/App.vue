<template>
 <div>
  <feedback-form/>
  
 </div>
 
</template>

<script>

import FeedbackForm from './components/FeedbackForm.vue'

export default {
  name: 'App',
  components: {
    FeedbackForm,
    
  }
}
</script>

<style>
*{
  font-size: 17px;
  font-weight:bold;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
</style>
