


<template>
    <div id="app">
    <img src="./assets/logo.png">
    <!-- <p :title='hello'>
      {{ hello }}
    </p> -->
   
    <p v-text="hello"></p>
  
    <p v-html="hello"></p>
  
   <!--组件列表渲染1-->
   
   <!--组件列表渲染2  对象-->
   <componenta v-for="(value,key) in objectList" :key="key"></componenta>
  <!--使用v-for 循环 技术盲点是怎么获取到每个集合元素的索引   集合-->
  <p v-for="item in list" :key="item.id"> {{ item.name }} - {{ item.price }} - {{ item.id }}</p> 
   
   <button v-on:click=addItem>addItem</button>
   <!--相当于v-bind:href -->
   <a :href="link" :title="Baidu">Link</a>
   
   <a v-if="isPartA">partA</a>
   <!--DOM 中存在 通过 css display none 给隐藏掉了-->
   <a v-show="!isPartA">partB</a>
   <button v-on:click="toggle">toggle</button>

   <!--自定义事件-->
   <componenta @my-event="onComaMyEvent"></componenta>
   
   <!--表单-->
   <input type="text" v-model="myValue" value="apple"/>
   <input type="radio" v-model="myBox" value="1"/>
   <input type="radio" v-model="myBox" value="2">
   <input type="radio" v-model="myBox" value="3">
   
   <select v-model="selection">
    <option value="1">1</option>
    <option value="2">2</option>
   </select>
    {{ selection }}
    {{ myBox }}
     <router-view/> 
  </div>

</template>

<script>
import componentA from './components/a'
import Vue from 'vue'
export default {
  //注册子组件a
  components: {
    componenta: componentA
    },
  data() {
      return {
        myValue: '',
        hello: 'world',
        selection: null,
        myBox:'',
        link: 'http://www.baidu.com',
        isPartA : true,
        Baidu: 'this is baidu',
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
   addItem () {
      Vue.set(this.list,1,{
        name: 'pinaapple',
        price: 256
      })
   },
   toggle() {
     var _this = this;
       _this.isPartA = ! _this.isPartA;
   },
   onComaMyEvent(param) {
    console.log('make the components random' + param);
    
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
