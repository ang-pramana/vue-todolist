<template>
    <div>
       <md-toolbar >
        <span style="color: white"><h2>List Todo</h2></span>
      </md-toolbar>
      <div>
        <form @submit.prevent="submitTodo" class="md-layout">
          <div class="md-layout md-gutter">
            <div class="md-layout-item md-small-size-70">
                <md-field >
                    <label for="name">Nama ToDo</label>
                    <md-input name="name" id="name" autocomplete="name" v-model="name"  />
                </md-field>
                </div>
                <div class="md-layout-item md-small-size-20">
                <md-field >
                    <label for="time">Time</label>
                    <md-input name="time" id="time" autocomplete="time" v-model="time"  />
                </md-field>
                <md-button type="submit" class="md-dense md-raised md-primary">Create</md-button>
                </div>
          </div>
        </form>
      </div>
      <br/>
      <div>
          <md-list v-for="todo in packages" :key="todo.id">
            <md-list-item >
                <div class="md-list-item-text">
                <span class="md-title">{{todo.name}}</span>
                <p><i>Time: {{todo.time}}</i></p>
                </div>
                <span>
                  <a @click.prevent="deleteTodo(todo)">
                    <i class="material-icons right teal-text">delete</i>
                  </a>
                </span>
            </md-list-item>

        </md-list>

      </div>
    </div>
</template>

<script>
export default {
  name: 'list-todo',
  data () {
    return {
      packages: [],
      name: null,
      time: null
    }
  },
  watch: {
    packages: {
      handler () {
        console.log('menambahkan ke localstorage')
        localStorage.packages = JSON.stringify(this.packages)
      },
      deep: true
    }
  },
  mounted () {
    console.log('mounted dipanggil')
    if (localStorage.packages) {
      this.packages = JSON.parse(localStorage.packages)
    }
  },
  methods: {
    submitTodo () {
      this.packages.push({
        name: this.name,
        time: this.time
      })
      this.name = null
      this.time = null
    },
    deleteTodo (todo) {
      const todoIndex = this.packages.indexOf(todo)
      this.packages.splice(todoIndex, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
  .md-list {
    width: 100%;
    max-width: 100%;
    display: inline-block;
    vertical-align: top;
    border: 1px solid rgba(#000, .12);
  }
  .md-toolbar {
    background: aqua;
  }
</style>
