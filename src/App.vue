<template>
  <div id="app">
    <FormList/>
  </div>
</template>

<script>
import MyForm from '@/components/MyForm'
import FormList from '@/components/nasted/FormList'
export default {
  name: 'App',
  components:{
    MyForm,
    FormList
  }
}
</script>
