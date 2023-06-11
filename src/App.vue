<template>
  <div id="app-container">
    <h1 v-color="color">App 根组件</h1>
    <p v-color="'red'">测试</p>

    <button @click="color = 'green'">改变 color 的颜色值</button>
    <hr/>
    <Article>
      <template #title>
        <h3>这是title插槽</h3>
      </template>
  
      <template #content="{msg, user}">
        <h3>
          这是content插槽
        </h3>
        <p>{{ msg }}</p>
        <p>{{ user.name }}</p>
      </template>

      <template #author>
        <h3>
          这是author插槽
        </h3>
      </template>
    </Article>

    <div class="box" style="display: none;">
      <!-- 渲染Left和Right组件 -->
      <Left>
          <!-- 1.如果要把内容填充到指定名称的插槽中，需要使用v-slot:这个指令 -->
         <!-- 2. v-slot:后面要跟上插槽的名字 -->
         <!-- 3.v-slot指令：不能直接用在元素身上，必须用在template标签上 -->
         <!-- 4.template这个标签，他是一个虚拟的标签，只起到包裹的作用，但是，不会被渲染为任何实质的html元素 -->
         <!-- 5.v-slot指令的简写形式是# -->
        <template #default>
         <!-- 默认情况下，在使用组件的时候，提供的内容都会被填充到名字为default的插槽之中 -->
         <p>这是在Left组件区域的内容，声明的p标签</p>
      </template>
      </Left>

    </div>
  </div>
</template>

<script>
import ArticleVue from './components/Article.vue'
import HelloWorld from './components/HelloWorld.vue'

import Left from './components/Left.vue'
import Right from './components/Right.vue'
import Article from './components/Article.vue'

export default {
  name: 'App',
  data() {
    return {
      color: 'blue'
    }
  },
  components: {
   Left,
   Right,
   Article
  },
  // 私有自定义指令的节点
  directives: {
    // 定义名为 color 的指令，指向一个配置对象
    color(el, binding) {
      // 当指令第一次被绑定到元素上的时候，会立即出发bind函数
      // 形参中的 el 表示当前指令所绑定到的那个 DOM对象
      // bind(el, binding) {
      //   console.log('触发了 v-color 的bind函数');
      //   el.style.color = binding.value
      // },
      // // 在DOM更新的时候，会触发update函数
      // update(el, binding) {
      //   console.log('触发了 v-color 的bind函数');
      //   el.style.color = binding.value
      // }

      el.style.color = binding.value
    }
  }
}
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.box {
  display: flex;
}
</style>
