<template>
  <div>
     模板输出显示：{{ message }}
     <br>
     {{ local }}
  </div>
</template>

<script>
   export default {
     name:'Echo',
     props:[
      'message'
     ],
     data() {
       return {

       }
     },
     computed:{
       local:function () {
         return 0+ this.message
       }
     }
   }
</script>
