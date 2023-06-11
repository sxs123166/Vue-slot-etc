<template>
  <div class="Left-container">
    <h3>Left组件</h3>
    <hr/>
    <!-- 声明一个插槽区域 -->
    <!-- vue官方规定：每一个slot插槽，都要有一个name名称 -->
    <!-- 如果省略了slot的name属性，则有一个默认名称叫做default -->
    <slot name="default">
        <h6>这是插槽里面的默认内容</h6>
    </slot>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.Left-container {
    display: block;
    flex: 1;
    padding: 0 20px;
    height: 500px;
    background-color: orange;
}
</style>