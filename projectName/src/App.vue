<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <p :title='hello'>
      {{ hello }}
    </p> -->
   
  <p v-text="hello"></p>
  <p v-html="hello"></p>
   <!--组件列表渲染1-->
   <componenta></componenta>
   <!--组件列表渲染2-->
   <componenta v-for="(value,key) in objectList" :key="key"></componenta>
  <!--使用v-for 循环 技术盲点是怎么获取到每个集合元素的索引-->
  <p v-for="item in list" :key="item.id"> {{ item.name }} - {{ item.price }} - {{ item.id }}</p> 
  
  <button v-on:click="addItem"></button>
    <router-view/>
  </div>
</template>

<script>
import componentA from './components/a'
export default {
  //注册子组件a
  components: {
    componenta: componentA
    },
  data() {
      return {
        hello: 'world',
        //集合
        list: [
          { id:'1',
            name: 'apple',
            price: 34
          },
          { id: '2',
            name: 'banana',
            price: 56
          }
        ],
        //对像
        objectList: {
          name: 'apple',
          price: 34,
          color: 'red',
          weight: 14
        }
      }
 },
  methods: {
    addItem (){
     var _this = this;
     _this.list.push({
       name: 'pinaapple',
       price: 56
     })
    }
  }

}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
