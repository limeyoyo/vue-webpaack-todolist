<template>
<div>
  <div>
    <input class="item" v-model="inputValue"/>
    <button @click="handleSubmit">提交</button>
  </div>
  <ul>
    <todo-item
      v-for="(item, index) of list"
      :key="index"
      :content="item"
      :index="index"
      @delete="handleDelete"
    >
    </todo-item>
  </ul>
</div>
</template>

<script>
import TodoItem from './components/TodoItem'
export default {
  // components: ['TodoItem']
  components: {
    'todo-item': TodoItem
  },
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handleSubmit () {
      // Vue的底层会自动把this的指向做一个变更，让this指向当前的实例。
      // this.$data.list
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handleDelete (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>
</style>
