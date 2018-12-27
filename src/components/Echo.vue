<template>
  <div>
     模板输出显示：{{ message }}
     <br>
     {{ local }}
     <section>
        向父级组件传递事件 通过 $emit()函数指定父级事件或属性,第二个值被当做参数传入第一个函数中
         <button @click='$emit("enlarge_text","第二个值可以传参")'>
            子集按钮
         </button>
     </section>
  </div>
</template>

<script>
   export default {
     name:'Echo',
     props:[
      'message',
      'enlarge_text',
      'searchText'
     ],
     data() {
       return {

       }
     },
     computed:{
       local:function () {
         return 0+ this.message
       }
     },
     methods:{

     }
   }
</script>
