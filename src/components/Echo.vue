<template>
  <div>
     模板输出显示：{{ message }}
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
          message:message.txt
       }
     },
   }
</script>
