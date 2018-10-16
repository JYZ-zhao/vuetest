<template>
  <div>
    <header class="site-header jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-xs-12">
            <h1>请发表对Vue的评论</h1>
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <!--将添加数据的方法传递给子组件，供子组件调用-->
      <Add :addComment="addComment"/>
      <!--将数据传递给子组件-->
      <List :comments="comments" :deleteComment="deleteComment"/>
    </div>
  </div>
</template>

<script>
  import Add from './components/Add'
  import List from './components/List'

  export default {

    data() {
      return {//数据应该使用ajax请求去后台查询
        comments: [//数据在哪个组件，操作数据的行为（方法）就应该定义在哪个组件

          {
            name: 'Bob',
            content: 'Vue 还不错'
          },
          {
            name: 'ZY ',
            content: 'Vue easy'
          },
          {
            name: 'ZZZ',
            content: 'Vue so so '
          },
          {
            name: 'WYN ',
            content: 'Vue nice'
          }
        ]
      }
    },
    methods: {
      //添加评论

      //将这个方法传递给子组件 :addComment="addComment"
      //实际开发中此方法应该与后台交互，提交ajax请求，修改数据库
      addComment(comment) {
        this.comments.unshift(comment)
      },

      //删除指定下标的评论
      deleteComment(index) {
        this.comments.splice(index, 1)
      }
    },
    components: {
      Add,
      List
    }
  }
</script>

<style>

</style>
