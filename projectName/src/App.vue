<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <p :title='hello'>
      {{ hello }}
    </p> -->
  <p v-text="hello"></p>
  <p v-html="hello"></p>
  <!--使用v-for 循环 技术盲点是怎么获取到每个集合元素的索引-->
  <p v-for="item in list" :key="item.id"> {{ item.name }} - {{ item.price }} - {{ item.id }}</p> 

    <router-view/>
  </div>
</template>

<script>
export default {
  data() {
      return {
        hello: 'world',
        list: [
          { id:'1',
            name: 'apple',
            price: 34
          },
          { id: '2',
            name: 'banana',
            price: 56
          }
        ]
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
