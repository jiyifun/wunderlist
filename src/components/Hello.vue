<template>
  <div class="wunder-task">
  <div class="add-item">
    <span class="add-icon">+</span>
    <input type="text" placeholder="添加任务..." v-model="newTask" @keyup.enter="addTask">
  </div>
  <ul class="todo-list">
    <li v-for="item in todoTasks" transition="expand"  @dblclick="removeTask(item)" :class="{finished:item.isFinished}">
      <input v-model="item.isFinished" type="checkbox"> {{item.msg}}
    </li>
  </ul>
  <div class="finished-list" >
    <button class="show-finished-btn" v-show="hasFinished" @click="toggleFinishedList">显示已完成</button>
    <ul class="todo-list finished" v-show="isFinishedShow">
      <li v-for="item in finishedTask" transition="expand"  @dblclick="removeTask(item)" :class="{finished:item.isFinished}">
        <input v-model="item.isFinished" type="checkbox"> {{item.msg}}
      </li>
    </ul>
  </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newTask: '', //新任务占位
      visibility: false, //过滤
      isFinishedShow: false,
      items:[
        {
          msg: 'first',
          isFinished: false
        },
        {
          msg: 'second',
          isFinished: false
        },
        {
          msg: 'third',
          isFinished: false
        }
      ]
    }
  },
  computed: {
    todoTasks: function() {
      return this.items.filter(function(v){
        return !v.isFinished;
      });
    },
    finishedTask: function() {
      return this.items.filter(function(v){
        return v.isFinished;
      });
    },
    hasFinished: function() {
      return this.finishedTask.length > 0;
    }
  },
  methods: {
    toggleItem: function(item) {
      item.isFinished = !item.isFinished;
    },
    toggleFinishedList: function(){
      this.isFinishedShow = !this.isFinishedShow;
    },
    addTask: function(){
      this.items.push({msg:this.newTask,isFinished:false});
      console.log('add item ' + this.newTask);
      this.newTask = '';
    },
    removeTask: function(item){
      console.log('remove ' + item.msg);
      var i,
          arr = this.items,
          len = arr.length;
      for (i = 0; i < len; i++) {
        if (arr[i] == item) {
          arr.splice(i,1);
          console.log('remove complited');
        };
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

/* 必需 */
.expand-transition {
  transition: all .3s ease;
  height: 40px;
  overflow: hidden;
}

/* .expand-enter 定义进入的开始状态 */
/* .expand-leave 定义离开的结束状态 */
.expand-enter, .expand-leave {
  height: 0;
  opacity: 0;
}

li,ul {
  margin: 0;
  padding: 0;
  list-style: none;
  color: #666;
}

.wunder-task {
  padding: 10px;
  text-align: left;
}

.add-item {
  padding: 5px;
  border-radius: 3px;
  background-color: rgba(102,137,100,0.75);
}

.add-item .add-icon {
  position: absolute;
  margin-left: 5px;
  margin-top: -2px;
  color: #fff;
  font-size: 28px;  
  line-height: 30px;
}
.add-item input {
  width: 100%;
  border: 0;
  outline: none;
  padding: 0 0 0 30px;
  border: none;
  line-height: 30px;
  background-color: transparent;
  color: #fff;
}
.todo-list {
  margin-top: 10px;
}

.todo-list li {
  padding-left: 10px; 
  margin:  1px 0;
  background-color: #fff;
  border-radius: 3px;
  line-height: 40px;
  vertical-align: middle;
}

li.finished {
  text-decoration: line-through;
  opacity: 0.5;
}
h1 {
  color: #42b983;
}

.show-finished-btn {
  margin-top: 10px; 
  padding: 3px 10px;
  background-color: rgba(102,137,100,0.75);
  color: #fff;
  border: none;
  border-radius: 3px;
  outline: none;
}
</style>
