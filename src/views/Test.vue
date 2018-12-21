
  <template >
   <div>
      {{ message }}

      <section>
          <button v-on:click="resolve">resolve</button>
      </section>

      <section>
         <Echo :message='test_msg'></Echo>
      </section>

      <div v-bind:id="dynamicId">rewrw</div>  //v-bind 绑定模板属性

      <p v-if="seen">现在你看到我了</p>

      <section style="color: green">
           计算属性赋值1：{{ math_message }}
          <p style="color: red"> 计算属性赋值2：{{ math_test_message }}</p>
          <input style="color:pink" v-model="question">
      </section>
   </div>
  </template>

<script>
    import Echo from '@/components/Echo'

    export default {  //一个vue对象
      name:'Test', //声明模板名称
      data() {   //绑定数据
        return {
          message: 'Hello Vue! this is my first app',
          dynamicId:false,
          seen:false,
          test_msg:'fuck!!!',
          question:''
        }
      },
      components:{ //引入模板
       Echo //模板传值
      },
      methods:{  //点击事件
       resolve:function () {
          this.message = "magic var"
          this.seen = !this.seen;
          this.test_msg = '我是爸爸，不服忍者'
       },
      },
      computed:{  // 计算属性的, 默认只有get方法,计算属性是基于它们的依赖进行缓存的,只在相关依赖发生改变时它们才会重新求值，比方法要快
         math_message: function () {  //
            return 1+1+30+52;
         },
         math_test_message: {
            get : function () {
                return  '我是爸爸';
            },
            set : function () {
                return '我是爸爸';
            }
         }
      },
      watch:{ //侦听属性  //监听事件
          question: function (newQuestion,oldQuestion) { //固定格式
            alert(newQuestion);
         }
      }
    }
</script>
