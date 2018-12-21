
  <template >
   <div>
      {{ message }}

      <section>
          <button v-on:click="resolve">resolve</button>
      </section>
      <section>
         <HelloWorld></HelloWorld>
      </section>
      <div v-bind:id="dynamicId">rewrw</div>
   </div>
  </template>

<script>
    import HelloWorld from '@/components/HelloWorld'

    export default({
      name:'Test',
      data() {
        return {
          message: 'Hello Vue! this is my first app',
          dynamicId:false
        }
      },
      components:{
       HelloWorld
      },
      methods:{
       resolve:function () {
          this.message = "magic var"
       },
      }
    })
</script>
