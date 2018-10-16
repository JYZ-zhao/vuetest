<template>
  <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 style='display: none'>暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group">
      <Item v-for="(comment ,index) in comments" :key="index" :comment="comment" :deleteComment="deleteComment" :index="index"/>
    </ul>
  </div>
</template>

<script>
  import Item from './Item'

  export default {
    //声明接收属性 :这个属性就会成为组件对象的属性 模版里就可以直接读取它 类似data
    //只是data是内部的
    //接收父组件传递的数据
    props: ['comments', 'deleteComment'],
    components: {
      Item
    }
  }
</script>

<style>
  .reply {
    margin-top: 0px;
  }
</style>
