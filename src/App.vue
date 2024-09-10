<!-- 模板 -->
<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/> -->

    <p>双向绑定：{{val1}}</p>
    <input type="text" name="" value="" v-model="val1">

    <p>单向绑定：{{val2}}</p>
    <input type="text" name="" :value="val2">
    <p>单向绑定：{{val2}}</p>
    <input type="text" name="" v-bind:value="val2">
    
    
    <button @click="btn">按钮</button>


    <p>{{val1 + '222'}}</p>
    <p>{{val1Change}}</p>
    <p>{{val1Change}}</p>


    <div>
      <ul>
        <li v-for="item in topBar" :key = "item.id" 
        :class="(action==item.id)?'action':''" 
        @click="selected(item.id)"
        > 
          {{item.title}}</li>
      </ul>
    </div>

    <h1 :style="{color:'red'}">绑定style1</h1>
    <h1 :style="style">绑定style2</h1>





  </div>
</template>

<!-- JS代码 -->
<script>
  

  export default {
    data(){

      return{

        style:{
          color:"blue",
        },

        action:1,
        topBar:[
          {id:1, title:"首页"},
          {id:2, title:"课程"},
          {id:3, title:"关于"},
        ],
        

        val1:"1111",
        val2:"2222"

      }
    },

    //对数据进行二次计算
    computed:{
      // val1Change:{
      //   console.log("计算val1");
      //   return this.val1 + "222";
      // }
      val1Change:{
        get(){
          console.log("get");
          return this.val1 + "222";
          
        },
        //可以修改val1
        set(val){
          console.log("set");
          this.val1 = val
        }

        
      }

    
    },

    methods:{

      selected(val){
        this.action = val;
      },
    
      btn(){
        // console.log(this.val1);
        // console.log(this.val2);

        console.log(this.val1Change);
        this.val1Change = "3333";

      }
    }
  }



</script>


<!-- 样式 -->
<style>

ul{
  list-style: none;
}

ul li{
  display: inline-block;
  margin: 20px;
}

.action{
  /* 字体加粗 */
  font-weight: bold;
  color: red;

}


/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
