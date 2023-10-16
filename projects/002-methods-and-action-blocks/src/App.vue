<template>
  <div>
    <h1>Methods and Action Blocks</h1>
    <div>
      <h2>Methods</h2>
      <p>The total amount is {{ total }}</p>
      <div>
        <button @click="calc(`+`)">Increase +</button>
        <button @click="calc(`-`)">Decrease -</button>
      </div>
    </div>
    <div>
      <h2>Computed Props</h2>
      <p>Formatted Name: {{ formattedName }}</p>
      <p>Formatted Name with Getters and Setters: {{ formattedNameV2 }}</p>
      <label> Insert user name: </label>
      <input type="text" v-model="userName" placeholder="name" />
      <button @click="formattedNameV2 = formattedNameV2.toUpperCase()">To Upper Case</button>
    </div>
    <div>
      <h2>Watchers</h2>
      <label>Query: </label>
      <input v-model="watchedField" type="text" placeholder="Type something" />
      <button @click="apiSimulator(watchedField)">🔍</button>
      <p>{{ watchResult }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { total: 0, userName: '', userName2: '', watchedField: null, watchResult: null }
  },
  methods: {
    calc(signal) {
      signal === '+' ? (this.total += 1) : (this.total -= 1)
    },
    apiSimulator(username) {
      this.watchResult = 'Start query'
      setTimeout(() => {
        this.watchResult = JSON.stringify(
          {
            username: username,
            password: Date.now().toString(),
            'validation-factors': {
              validationFactors: [
                {
                  name: 'remote_address',
                  value: '127.0.0.1',
                },
              ],
            },
          },
          null,
          4
        )
      }, 2500)
    },
  },
  computed: {
    formattedName() {
      console.log('run computed props')
      const lowerCase = this.userName.toLowerCase()
      const names = lowerCase.split(' ')
      const capitalizedNames = names.map((name) => {
        if (name.length === 0) {
          return ''
        }
        return name.charAt(0).toUpperCase() + name.slice(1)
      })
      return capitalizedNames.join(' ')
    },
    formattedNameV2: {
      get: function () {
        console.log('run getter')
        const lowerCase = this.userName.toLowerCase()
        const names = lowerCase.split(' ')
        const capitalizedNames = names.map((name) => {
          if (name.length === 0) {
            return '' // Skip empty words
          }
          return name.charAt(0).toUpperCase() + name.slice(1)
        })
        return capitalizedNames.join(' ')
      },
      set: function (updatedValue) {
        console.log('run setter')
        this.userName = updatedValue
      },
    },
  },
  watch: {
    watchedField() {
      this.watchResult = 'Input detected'
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 10px;
  padding: 10px;
}
</style>
