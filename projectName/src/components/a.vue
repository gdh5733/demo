<template>
     <div>
         {{ msg }}

         <button @click="emitClick">emitClick</button>
     </div>
</template>

<script>
export default{

 data() {
     return {
         msg: 'this a vue components is test successful!',
         hello: 'hello worlllld'
     }
 },
 methods: {

     emitClick () {
      var _this = this;
      _this.$emit(my-event,_this.hello);
     }
   
 }
}
</script>
<style scoped>
</style>

