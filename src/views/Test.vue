
  <template >
   <div>
      {{ message }}

      <section>
          <button v-on:click="resolve">resolve</button>
      </section>

      <section>
         <Echo :message='test_msg' @enlarge_text="childce" ></Echo>
      </section>

      <div v-bind:id="dynamicId">rewrw</div>  //v-bind 绑定模板属性

      <p v-if="seen">现在你看到我了</p>

      <section style="color: green">
           计算属性赋值1：{{ math_message }}
          <p style="color: red"> 计算属性赋值2：{{ math_test_message }}</p>
          <input style="color:pink" v-model="question">
      </section>
      <section>
           <button style="color:red" @click="button(test_button_param)">红色按钮</button>
      </section>

      <section>
          <p :class='classObject'>
             测试类属性
          </p>
          <p :class='[{active:isActive},errorClass]'>
             测试类属性数组语法
          </p>
      </section>
      <section>
         复选框

        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">{{ checked }}</label>

        <div>
           多个复选框
            <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
            <label for="jack">Jack</label>
            <input type="checkbox" id="john" value="John" v-model="checkedNames">
            <label for="john">John</label>
            <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
            <label for="mike">Mike</label>
            <br>
            <span>Checked names: {{ checkedNames }}</span>
        </div>

      </section>

      <section>
        <div>
           单选框
          <input type="radio"  value="One" v-model="picked">
          <label for="one">One</label>
          <br>
          <input type="radio"  value="Two" v-model="picked">
          <label for="two">Two</label>
          <br>
          <span>Picked: {{ picked }}</span>
        </div>

      </section>
      <section>
           选择框
           <div>
              <select v-model="selected">
                <!-- 在 iOS 中，这会使用户无法选择第一个选项。因为这样的情况下，iOS 不会触发 change 事件。因此，更推荐像上面这样提供一个值为空的禁用选项。 -->
              <option disabled value="">请选择</option>
              <option>A</option>
              <option>B</option>
              <option>C</option>
              </select>
              <span>Selected: {{ selected }}</span>
           </div>
      </section>
      <section>
        <AlertBox :message='alert'></AlertBox>
      </section>
   </div>
  </template>

<script>
    import Echo from '@/components/Echo'
    import AlertBox from '@/components/AlertBox'

    export default {  //一个vue对象
      name:'Test', //声明模板名称
      data() {   //绑定数据
        return {
          message: 'Hello Vue! this is my first app',
          dynamicId:false,
          seen:false,
          test_msg:'fuck!!!',
          question:'',
          isActive:true,
          checked:false,
          checkedNames:[],
          picked:'',
          selected:'',
          searchText:'',
          alert:'你错啦！！！'

        }
      },
      components:{ //引入模板
       Echo,AlertBox //模板传值
      },
      methods:{  //点击事件
       resolve:function () {
          this.message = "magic var"
          this.seen = !this.seen;
          this.test_msg = '我是爸爸，不服忍者'
       },
       button:function ($message){
         alert($message);
       },
       childce:function(message){
         alert(message);
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
         },
         classObject :function () {
            return {
              active:true,
              testsss:true
            }
         },
         errorClass :function () {
           return false;
         },
         test_button_param : function(){
           return 'test';
         },
      },
      watch:{ //侦听属性  //监听事件
          question: function (newQuestion,oldQuestion) { //固定格式
            alert(newQuestion);
          },
          checked : function (newChecked,oldChecked) {
            $this.checked=newChecked;
          },
          checkedNames: function (newCheckedNames,oldCheckedNames){
             this.checkedNames=newCheckedNames;
          },
          picked : function(newPicked,oldPicked){
             this.picked = newPicked;
          },
          selected : function(newSelected,oldSelected){
             this.selected = newSelected;
          },
          searchText:function(newSearchText,oldSearchText){
              alert(newSearchText);
         }
      }
    }
</script>
