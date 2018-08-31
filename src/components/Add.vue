<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input type="text" class="form-control" placeholder="用户名" v-model="name">
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea class="form-control" rows="6" placeholder="评论内容" v-model="content"></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="button" class="btn btn-default pull-right" @click="add">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  export default {

    //props 可以是数组或对象，用于接收来自父组件的数据。
    // props 可以是简单的数组，或者使用对象作为替代，
    // 对象允许配置高级选项，如类型检测、自定义校验和设置默认值。
    //接收父组件传递的添加评论的方法，调用
    props: {
      addComment: {
        //类型为方法
        type: Function,
        //必要性
        required: true
      }
    },
    //一个组件的data必须是函数
    data() {
      return {
        name: '',
        content: ''
      }
    },
    methods: {
      add() {
        //1.检查输入的合法性
        const name = this.name.trim()
        const content = this.content.trim()
        if (!name || !content) {
          alert("姓名或内容不能为空")
          return
        }
        //2.根据输入的数据，封装成comment对象
        const comment = {
          name,
          content
        }
        //3.添加到comments中
        //使用父组件提供的方法添加到comments
        this.addComment(comment)

        //4.清除输入
        this.name = ''
        this.content = ''

      }
    }
  }
</script>

<style>

</style>
